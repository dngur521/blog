# 1일차
- 아두이노에 IR 송수신 모듈 달아서 에어컨 리모컨의 값 확인해서 저장
- 아두이노 시리얼에 ```SEND 1,2``` 이런식으로 처음 값은 에어컨 모드 종류, 두번째 값은 보내는 반복 횟수로 전송하면 그에 맞는 동작 수행
- 이를 라즈베리파이에 연결해 라즈베리파이에서 아두이노로 시리얼을 통해 값을 보내면 에어컨이 작동되게 함


# 1일차 작동 영상 (유튜브 링크)
[![유튜브 링크](http://i.ytimg.com/vi/BpOoKStL1qM/maxresdefault.jpg)](https://youtu.be/BpOoKStL1qM?si=jRJ2ZUoAFz-E9UFn)

# 1일차 코드
<details>
  <summary>- 아두이노</summary>

```C
#include <IRremote.h>
#include <IRremoteInt.h> 

// IR LED가 연결된 핀 번호
#define IR_SEND_PIN 11

// IR 발신 객체 생성
IRsend irsend(IR_SEND_PIN);

// 에어컨 모드와 온도에 해당하는 IR 명령어들을 배열로 저장
// 0부터 시작하는 인덱스가 SEND 명령어의 첫 번째 숫자와 매칭된다
// 예: codes[0] = 냉방.약풍, 18도
const unsigned long codes[] = {
  0x880, // 냉방. 약풍, 18도
  0x840, // 냉방. 약풍, 19도
  0x850, // 냉방. 약풍, 20도
  0x860, // 냉방. 약풍, 21도
  0x870, // 냉방. 약풍, 22도
  0x880, // 냉방. 약풍, 23도
  0x890, // 냉방. 약풍, 24도
  0x8A0, // 냉방. 약풍, 25도
  0x8B0, // 냉방. 약풍, 26도
  0x8C0, // 냉방. 약풍, 27도
  0x8D0, // 냉방. 약풍, 28도
  0x8E0, // 냉방. 약풍, 29도
  0x8F0, // 냉방. 약풍, 30도
  0x832, // 냉방. 중풍, 18도
  0x842, // 냉방. 중풍, 19도
  0x852, // 냉방. 중풍, 20도
  0x862, // 냉방. 중풍, 21도
  0x872, // 냉방. 중풍, 22도
  0x882, // 냉방. 중풍, 23도
  0x892, // 냉방. 중풍, 24도
  0x8A2, // 냉방. 중풍, 25도
  0x8B2, // 냉방. 중풍, 26도
  0x8C2, // 냉방. 중풍, 27도
  0x8D2, // 냉방. 중풍, 28도
  0x8E2, // 냉방. 중풍, 29도
  0x8F2, // 냉방. 중풍, 30도
  0x834, // 냉방. 강풍, 18도
  0x844, // 냉방. 강풍, 19도
  0x854, // 냉방. 강풍, 20도
  0x864, // 냉방. 강풍, 21도
  0x874, // 냉방. 강풍, 22도
  0x884, // 냉방. 강풍, 23도
  0x894, // 냉방. 강풍, 24도
  0x8A4, // 냉방. 강풍, 25도
  0x8B4, // 냉방. 강풍, 26도
  0x8C4, // 냉방. 강풍, 27도
  0x8D4, // 냉방. 강풍, 28도
  0x8E4, // 냉방. 강풍, 29도
  0x8F4, // 냉방. 강풍, 30도
  0x835, // 냉방. 자동풍, 18도
  0x845, // 냉방. 자동풍, 19도
  0x855, // 냉방. 자동풍, 20도
  0x865, // 냉방. 자동풍, 21도
  0x875, // 냉방. 자동풍, 22도
  0x885, // 냉방. 자동풍, 23도
  0x895, // 냉방. 자동풍, 24도
  0x8A5, // 냉방. 자동풍, 25도
  0x8B5, // 냉방. 자동풍, 26도
  0x8C5, // 냉방. 자동풍, 27도
  0x8D5, // 냉방. 자동풍, 28도
  0x8E5, // 냉방. 자동풍, 29도
  0x8F5, // 냉방. 자동풍, 30도
  0x930, // 제습. 약풍, 18도
  0x940, // 제습. 약풍, 19도
  0x950, // 제습. 약풍, 20도
  0x960, // 제습. 약풍, 21도
  0x970, // 제습. 약풍, 22도
  0x980, // 제습. 약풍, 23도
  0x990, // 제습. 약풍, 24도
  0x9A0, // 제습. 약풍, 25도
  0x9B0, // 제습. 약풍, 26도
  0x9C0, // 제습. 약풍, 27도
  0x9D0, // 제습. 약풍, 28도
  0x9E0, // 제습. 약풍, 29도
  0x9F0, // 제습. 약풍, 30도
  0x932, // 제습. 중풍, 18도
  0x942, // 제습. 중풍, 19도
  0x952, // 제습. 중풍, 20도
  0x962, // 제습. 중풍, 21도
  0x972, // 제습. 중풍, 22도
  0x982, // 제습. 중풍, 23도
  0x992, // 제습. 중풍, 24도
  0x9A2, // 제습. 중풍, 25도
  0x9B2, // 제습. 중풍, 26도
  0x9C2, // 제습. 중풍, 27도
  0x9D2, // 제습. 중풍, 28도
  0x9E2, // 제습. 중풍, 29도
  0x9F2, // 제습. 중풍, 30도
  0x934, // 제습. 강풍, 18도
  0x944, // 제습. 강풍, 19도
  0x954, // 제습. 강풍, 20도
  0x964, // 제습. 강풍, 21도
  0x974, // 제습. 강풍, 22도
  0x984, // 제습. 강풍, 23도
  0x994, // 제습. 강풍, 24도
  0x9A4, // 제습. 강풍, 25도
  0x9B4, // 제습. 강풍, 26도
  0x9C4, // 제습. 강풍, 27도
  0x9D4, // 제습. 강풍, 28도
  0x9E4, // 제습. 강풍, 29도
  0x9F4, // 제습. 강풍, 30도
  0x935, // 제습. 자동풍, 18도
  0x945, // 제습. 자동풍, 19도
  0x955, // 제습. 자동풍, 20도
  0x965, // 제습. 자동풍, 21도
  0x975, // 제습. 자동풍, 22도
  0x985, // 제습. 자동풍, 23도
  0x995, // 제습. 자동풍, 24도
  0x9A5, // 제습. 자동풍, 25도
  0x9B5, // 제습. 자동풍, 26도
  0x9C5, // 제습. 자동풍, 27도
  0x9D5, // 제습. 자동풍, 28도
  0x9E5, // 제습. 자동풍, 29도
  0x9F5, // 제습. 자동풍, 30도
};

void setup() {
  Serial.begin(9600); 
  Serial.println("아두이노가 준비되었습니다. 'SEND <숫자1>,<숫자2>'를 입력하세요.");
  Serial.println("예: SEND 0,2 (냉방 약풍 18도 신호를 2번 반복)");
}

void loop() {
  // 시리얼 포트에 데이터가 들어왔는지 확인
  if (Serial.available()) { 
    // 시리얼 포트에서 한 줄을 읽어 문자열로 저장
    String input = Serial.readStringUntil('\n'); 
    input.trim();

    // 입력이 "SEND"로 시작하는지 확인
    if (input.startsWith("SEND ")) {
      // "SEND " 부분을 제거하여 숫자 부분만 남김
      String data = input.substring(5);
      
      // 쉼표(,) 위치를 찾기
      int commaIndex = data.indexOf(',');
      
      // 쉼표가 존재하는지 확인
      if (commaIndex > 0) {
        // 첫 번째 숫자(인덱스)와 두 번째 숫자(반복 횟수)를 파싱
        String indexStr = data.substring(0, commaIndex);
        String repeatsStr = data.substring(commaIndex + 1);
        
        int index = indexStr.toInt();
        int repeats = repeatsStr.toInt();

        // 인덱스 값이 유효한지 확인 (배열의 범위를 넘지 않는지)
        if (index >= 0 && index < sizeof(codes) / sizeof(codes[0])) {
          // IR 신호 전송
          unsigned long command = codes[index];
          irsend.sendLG(0x88, command, repeats);
          
          Serial.print("IR 신호 전송 완료: Command=0x");
          Serial.print(command, HEX);
          Serial.print(", Repeats=");
          Serial.println(repeats);
        } else {
          Serial.println("잘못된 인덱스입니다. 0부터 103 사이의 숫자를 입력하세요.");
        }
      } else {
        Serial.println("잘못된 입력 형식입니다. 'SEND <숫자1>,<숫자2>' 형식으로 입력하세요.");
      }
    } else {
      Serial.println("잘못된 명령어입니다. 'SEND'로 시작하는 명령어를 입력하세요.");
    }
  }
}
```
</details>

<details>
  <summary>- 라즈베리파이</summary>

```python
import serial
import time

# 아두이노 시리얼 포트와 전송 속도(Baud Rate) 설정
SERIAL_PORT = '/dev/ttyUSB0'
BAUD_RATE = 9600

def send_command(ser, command):
    try:
        # 명령어에 줄바꿈 문자('\n')를 추가하고, 바이트로 인코딩하여 전송
        ser.write(f'{command}\n'.encode('utf-8'))
        print(f"Command sent: {command}")
        
        # 아두이노의 응답을 기다리기, timeout 설정으로 무한 대기를 방지합니다.
        response = ser.readline().decode('utf-8').strip()
        print(f"Arduino response: {response}")
        return response
        
    except serial.SerialException as e:
        print(f"Error communicating with Arduino: {e}")
        return None

# 메인 실행 코드
if __name__ == "__main__":
    try:
        # 시리얼 통신 객체 생성
        ser = serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=1)
        time.sleep(2)  # 아두이노와의 연결이 안정될 때까지 잠시 대기
        print(f"Connected to Arduino on {SERIAL_PORT}")
        while True:
            # 'SEND 1,2' 명령어 전송 (냉방. 약풍, 18도 신호를 2번 반복)
            send_command(ser, 'SEND 0,2')
            time.sleep(3)
            send_command(ser, 'SEND 50,2') # 제습. 약풍, 18도 신호를 2번 반복
            time.sleep(3)
        
    except serial.SerialException as e:
        print(f"Could not open serial port {SERIAL_PORT}: {e}")
        
    finally:
        if 'ser' in locals() and ser.is_open:
            ser.close()
            print("Serial port closed.")
```

</details>

# 2일차
- 라즈베리파이와 아두이노는 1일차때와 같이 시리얼 통신으로 진행
- React + Node.js로 라즈베리파이와 통신하여 에어컨 제어 및 온습도 값 보여주기 수행
- 라즈베리파이와 Node.js는 http로 통신
- 에어컨 제어할때 마다 라즈베리파이의 데이터베이스에 History 저장
- 온도도 1분마다 데이터베이스에 저장 준비 완료 (현 시점에서는 센서가 고장나있어서 테스트로 몇개만 해봄)
- 나중에 React에서 History 보는 기능 추가 예정
![실행화면1](https://i.ibb.co/YFnWq0xQ/2025-08-31-231933.png)
![실행화면2](https://i.ibb.co/Ld9tp6yk/2025-08-31-231937.png)

[![유튜브 링크](http://i.ytimg.com/vi/N_m-jxU_BFM/maxresdefault.jpg)](https://youtu.be/N_m-jxU_BFM?si=dDMILu6Gl6r_tCkq)