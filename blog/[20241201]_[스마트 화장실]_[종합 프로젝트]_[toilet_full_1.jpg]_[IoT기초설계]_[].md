# 전체적인 설계
- 라즈베리파이 및 GrovePi, 아두이노 사용
- 초음파센서, 버튼, 부저, 서보모터 → 아두이노
- 온습도센서, LED, LCD, 릴레이(Fan) → 라즈베리파이
- 시리얼 통신으로 아두이노와 라즈베리파이가 텍스트로 통신
- 각 센서 값들에 따라 각종 액추에이터들이 동작
![전체샷1](/img/smart_toilet/toilet_full_1.jpg)
![전체샷2](/img/smart_toilet/toilet_full_2.jpg)
![전체샷3](/img/smart_toilet/toilet_full_3.jpg)


# 구현 내용
화장실 내부의 사람 감지 (초음파 센서 사용)
→ 사람 들어오면 전등(LED) 및 릴레이(Fan) 동작
![구현 내용 1](/img/smart_toilet/act_1.jpg)

화장실 외부에 LCD 패널로 변기칸 사용 유무 및 온습도 체크
→ 실시간으로 업데이트 됨
![구현 내용 2](/img/smart_toilet/act_2.jpg)

현재 온습도에 따라 환풍기 자동 스위칭 (릴레이 및 온습도 센서)
→ 특정 온습도 이상이면 사람 유무에 관계없이 항상 환풍기 켜짐
![구현 내용 3](/img/smart_toilet/act_3.jpg)

변기 칸 사람 감지 및 사용 중 음악 재생 (초음파 센서)
변기 사용 이후 자동 뚜껑 닫기 및 물 내리기 (버튼 및 서보모터)
→ pygame 라이브러리 사용해서 음악 재생, 버튼 누르면 부저 소리와 함께 뚜껑이 닫힘
![구현 내용 4](/img/smart_toilet/act_4.jpg)

# 작동 영상 (유튜브 링크)
[![유튜브 링크](http://i.ytimg.com/vi/Zl0-rDz1aHA/maxresdefault.jpg)](https://youtu.be/Zl0-rDz1aHA)

# 코드 - 아두이노
```C
#include <Servo.h>   

// 핀 설정
const int TRIG_A = 10;
const int ECHO_A = 11;
const int TRIG_B = 3;
const int ECHO_B = 4;
const int TRIG_C = 6;
const int ECHO_C = 7;
const int BUZZER = 5;
   
const int buttonPin = 8;

bool toiletStatus = false;     // 이전 상태 추적
 
const int debounceDelay = 50;  // 디바운싱 시간 (밀리초)

bool buttonState     = HIGH;   // 현재 버튼 상태
bool lastButtonState = HIGH;   // 이전 버튼 상태

unsigned long lastDebounceTime = 0; // 마지막 디바운싱 시간

Servo servomotor;
const int servoPin = 9;

// 거리 측정 임계값 (cm)
const int DIST_THRESHOLD = 7;
const int DIST_TOILET    = 15;

// 카운트 변수
volatile int peopleCount = 0;

// 상태 정의
enum State {
  IDLE,
  A_DETECTED,
  B_DETECTED
};

State currentState = IDLE;

// 마지막 측정 시간 (디바운싱용)
unsigned long lastMeasurementTime = 0;
const unsigned long MEASUREMENT_INTERVAL = 100; // 0.01초

void setup() {
  // 시리얼 통신 시작
  Serial.begin(9600);
  
  // 트리거 핀을 출력으로, 에코 핀을 입력으로 설정
  pinMode(TRIG_A, OUTPUT);
  pinMode(ECHO_A, INPUT);
  pinMode(TRIG_B, OUTPUT);
  pinMode(ECHO_B, INPUT);
  pinMode(TRIG_C, OUTPUT);
  pinMode(ECHO_C, INPUT);
  pinMode(BUZZER, OUTPUT);
  pinMode(buttonPin, INPUT_PULLUP);
  
  // 트리거 핀을 LOW로 초기화
  digitalWrite(TRIG_A, LOW);
  digitalWrite(TRIG_B, LOW);
  digitalWrite(TRIG_C, LOW);

  digitalWrite(BUZZER, LOW);

  servomotor.attach(servoPin);
  
  delay(100); // 센서 초기화를 위한 지연
}
// 변기 물 내리는 함수, 부저로 대체함
void flushToilet() {
  digitalWrite(BUZZER, HIGH);
  delay(100);
  digitalWrite(BUZZER, LOW);
}

// 초음파센서로 거리 측정하는 함수
long measureDistance(int trigPin, int echoPin) {
  // 트리거 핀을 LOW로 설정하여 센서 초기화
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  
  // 트리거 핀을 HIGH로 10us 동안 유지하여 신호 전송
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Echo 핀으로부터 신호가 돌아올 때까지 대기
  long duration = pulseIn(echoPin, HIGH, 30000); // 타임아웃 설정 (30ms)
  
  // 거리를 계산 (cm 단위)
  long distance = duration * 0.034 / 2;
  
  return distance;
}

void loop() {
  unsigned long currentTime = millis();
  
  
  // 디바운싱: 일정 시간 간격으로만 측정
  if (currentTime - lastMeasurementTime >= MEASUREMENT_INTERVAL) {
    lastMeasurementTime = currentTime;
    
    // 센서 A 거리 측정
    long distanceA = measureDistance(TRIG_A, ECHO_A);

    // 센서 B 거리 측정
    long distanceB = measureDistance(TRIG_B, ECHO_B);
    
    // 센서 C 거리 측정
    long distanceC = measureDistance(TRIG_C, ECHO_C);
    //Serial.println(distanceC);
    // 센서 감지 여부
    bool detectedA = distanceA < DIST_THRESHOLD;
    bool detectedB = distanceB < DIST_THRESHOLD;
    
    // switch문을 이용한 현재 상태에 따른 인원 카운트 동작 코드
    switch (currentState) {
      case IDLE:
        if (detectedA && !detectedB) {
          currentState = A_DETECTED;
        }
        else if (detectedB && !detectedA) {
          currentState = B_DETECTED;
        }
        break;
        
      case A_DETECTED:
        if (detectedB) {
          peopleCount++;
          Serial.print("IN: ");
          Serial.println(peopleCount);
          currentState = IDLE;
        }
        else if (!detectedA) {
          currentState = IDLE; // 센서 A 감지 후 아무것도 안 감지되면 초기화
        }
        break;
        
      case B_DETECTED:
        if (detectedA) {
          if (peopleCount > 0) { // 사람 수가 0 이하로 내려가지 않도록
            peopleCount--;
            Serial.print("OUT: ");
            Serial.println(peopleCount);
          }
          currentState = IDLE;
        }
        else if (!detectedB) {
          currentState = IDLE; // 센서 B 감지 후 아무것도 안 감지되면 초기화
        }
        break;
        
      default:
        currentState = IDLE;
        break;
    }

    if (distanceC < DIST_TOILET && !toiletStatus) {
    Serial.println("TOILET:1");
    toiletStatus = true; // 상태 업데이트
    servomotor.write(180);
    } 
    else if (distanceC >= DIST_TOILET && toiletStatus) {
      Serial.println("TOILET:0");
      toiletStatus = false; // 상태 업데이트
      servomotor.write(85);
    }
    else if (distanceC == 0) {
      toiletStatus = true;
      servomotor.write(180);
    }
  }
  int reading = digitalRead(buttonPin); // 버튼 상태 읽기

  // 버튼 상태가 변경되었는지 확인
  if (reading != lastButtonState) {
    lastDebounceTime = millis(); // 상태 변경 시 시간 기록
  }

  // 디바운싱 처리
  if ((millis() - lastDebounceTime) > debounceDelay) {
    // 디바운싱 시간 이후에도 상태가 동일하다면
    if (reading != buttonState) {
      buttonState = reading; // 버튼 상태 업데이트

      if (buttonState == LOW) { // 버튼이 눌린 순간
        Serial.println("BUTTON:1");
        servomotor.write(85);
        flushToilet();
      }
    }
  }
  lastButtonState = reading; // 이전 상태 업데이트
}
```

# 코드 - 라즈베리파이
```python
import time
import sys
import grovepi
import RPi.GPIO as GPIO
import serial
import threading
import math
import os
import pygame
from grovepi import *

# Grovepi 설정
grovepi.set_bus("RPI_1")

ledMain      = 8
tempHumiSens = 7
relay        = 2

pinMode(ledMain, "OUTPUT")
pinMode(relay,   "OUTPUT")

# output 초기화
grovepi.digitalWrite(ledMain, 0)
grovepi.digitalWrite(relay,   0)

# GPIO 설정
GPIO.setmode(GPIO.BCM)

# 시리얼 포트 설정
SERIAL_PORT = '/dev/ttyUSB0'
BAUD_RATE   = 9600

# 시리얼 연결
ser = serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=1)
time.sleep(2)  # 시리얼 연결 안정화 대기

# 변수 초기화
current_count = 0
toilet_count  = 0

temp = 0
humi = 0
DHT11Val = [temp, humi]

# 변기칸 사용중 나오는 음악 초기화
pygame.mixer.init()
sound_sample = pygame.mixer.music
sound_sample.load('/home/pi/Desktop/longclassic.mp3')
sound_sample.play()
sound_sample.pause()

# I2C 디스플레이 초기화
if sys.platform == 'uwp':
    import winrt_smbus as smbus
    bus = smbus.SMBus(1)
else:
    import smbus
    rev = GPIO.RPI_REVISION
    if rev == 2 or rev == 3:
        bus = smbus.SMBus(1)
    else:
        bus = smbus.SMBus(0)

# I2C 주소 설정
DISPLAY_RGB_ADDR  = 0x62
DISPLAY_TEXT_ADDR = 0x3e
    
# RGB 설정 함수
def setRGB(r, g, b):
    bus.write_byte_data(DISPLAY_RGB_ADDR, 0, 0)
    bus.write_byte_data(DISPLAY_RGB_ADDR, 1, 0)
    bus.write_byte_data(DISPLAY_RGB_ADDR, 0x08, 0xaa)
    bus.write_byte_data(DISPLAY_RGB_ADDR, 4, r)
    bus.write_byte_data(DISPLAY_RGB_ADDR, 3, g)
    bus.write_byte_data(DISPLAY_RGB_ADDR, 2, b)

# 이 밑으로 디스플레이 텍스트 설정하는 함수들
def textCommand(cmd):
    bus.write_byte_data(DISPLAY_TEXT_ADDR, 0x80, cmd)

def setText(temp_humi, count):
    try:
        textCommand(0x01)  # 화면 지우기
        time.sleep (0.01)   
        textCommand(0x08 | 0x04)  # 화면 켜기, 커서 없음

        # 첫 번째 줄: 온도와 습도
        for c in temp_humi:
            bus.write_byte_data(DISPLAY_TEXT_ADDR, 0x40, ord(c))
            
    except IOError:
        print("IOError")
        
def setText2(count):
    try:
        textCommand(0x28)  # 2줄
        time.sleep (0.01)
        
        # 두 번째 줄: 현재 사람 수
        textCommand(0xc0)  # 두 번째 줄로 이동
        count_text = "Usage: {}".format(count)
        
        for c in count_text:
            bus.write_byte_data(DISPLAY_TEXT_ADDR, 0x40, ord(c))
            
    except IOError:
        print("IOError")

# 온습도센서에서 온습도 읽어들여서 디스플레이에 나타내는 함수
def getDHT11():
    global current_count
    global DHT11Val
    while True:
        try:
            DHT11Val[0], DHT11Val[1] = grovepi.dht(tempHumiSens, 0)
            
            if not math.isnan(DHT11Val[0]) and not math.isnan(DHT11Val[1]):
                temp_humi_text = "{}C, {}%".format(DHT11Val[0], DHT11Val[1])
                setText(temp_humi_text, toilet_count)
                
            setText2(toilet_count)
            
            time.sleep(.5)  # 데이터 수집 주기
        except IOError:
            continue
        
# 변기 물 내리는 함수, 여기서는 부저로 대체함
def flushToilet():
    print("물 내려감")

# 시리얼통신으로 연결된 아두이노에서 나오는 값 읽어들이는 함수
def getSerialVal():
    global current_count
    global toilet_count
    
    while True:
        if ser.in_waiting > 0:
            line = ser.readline().decode('utf-8').rstrip()
            if line:
                if line.startswith("IN:"):
                    try:
                        count = int(line.split(":")[1].strip())
                        current_count = count
                        print(f"사람이 들어왔습니다. 현재 인원: {current_count}")
                    except ValueError:
                        print(f"잘못된 데이터 형식: {line}")
                    except TypeError:
                        continue
                    
                elif line.startswith("OUT:"):
                    try:
                        count = int(line.split(":")[1].strip())
                        current_count = count
                        print(f"사람이 나갔습니다. 현재 인원: {current_count}")
                    except ValueError:
                        print(f"잘못된 데이터 형식: {line}")
                    except TypeError:
                        continue
                    
                elif line.startswith("TOILET:"):
                    try:
                        toiletcount  = int(line.split(":")[1].strip())
                        toilet_count = toiletcount
                        if (toiletcount == 1):
                            print(f"변기칸사람들어옴.{toilet_count}")
                        else:
                            print(f"변기칸사람나감.{toilet_count}")
                    except ValueError:
                        print(f"잘못된 데이터 형식: {line}")
                    except TypeError:
                        continue
                    
                elif line.startswith("BUTTON"):
                    try:
                        flushToilet()
                    except ValueError:
                        print(f"잘못된 데이터 형식: {line}")
                    except TypeError:
                        continue      
                        
        time.sleep(0.1)  # CPU 사용량 줄이기 위한 짧은 대기
        
# 메인 led와 릴레이 제어하는 함수
def controlMainLamp():
    global current_count
    global toilet_count
    global DHT11Val
    
    while True:
        try:
            if (not (math.isnan(DHT11Val[0]))):
                temp = DHT11Val[0]
            
            if (not (math.isnan(DHT11Val[1]))):
                humi = DHT11Val[1]
                
            if current_count >= 1:
                digitalWrite(ledMain, 1)
                digitalWrite(relay,   1)
                setRGB(0, 100, 0)
                
            elif (current_count == 0):
                digitalWrite(ledMain, 0)
                
                if ((temp > 30) or (humi > 40)):
                    digitalWrite(relay, 1)
                    
                else:
                    digitalWrite(relay, 0)
                
            if (toilet_count == 1):
                setRGB(100, 100, 0)
            
            if (toilet_count == 0):
                setRGB(0, 100, 0)
            
        except IOError:
            continue

# 변기칸에 사람 있으면 음악 재생하는 함수
def music_Play():
    while True:
        try: 
            if(toilet_count == 1): 
                sound_sample.unpause()
            else:
                sound_sample.pause()
            time.sleep(.05)
        except Exception as e:
            print ("Error:{}".format(e))
      
try:
    # 쓰레드 생성
    dht_thread      = threading.Thread(target=getDHT11)
    serial_thread   = threading.Thread(target=getSerialVal)
    mainLamp_thread = threading.Thread(target=controlMainLamp)
    music_thread    = threading.Thread(target=music_Play)

    # 쓰레드 시작
    dht_thread.start()
    mainLamp_thread.start()
    serial_thread.start()
    music_thread.start()

    # 쓰레드가 종료될 때까지 대기
    dht_thread.join()
    serial_thread.join()
    mainLamp_thread.join()
    music_thread.join()
    
except IOError:
    print("IOError")

except ZeroDivisionError:
    print("0으로 나눴음")
    
except KeyboardInterrupt:
    dht_thread.stop()
    mainLamp_thread.stop()
    serial_thread.stop()
    music_thread.stop()

finally:
    ser.close()
    GPIO.cleanup()

```