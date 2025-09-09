# 5097. [파이썬 S/W 문제해결 기본] 6일차 - 회전
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&problemLevel=3&problemLevel=4&contestProbId=AWTVjgHKbn8DFAVT&categoryId=AWTVjgHKbn8DFAVT&categoryType=CODE&problemTitle=&orderBy=PASS_RATE&selectCodeLang=ALL&select-1=4&pageSize=10&pageIndex=1)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    # N, M을 입력 받습니다.
    N, M = map(int, input().split())
    
    # 여러 개의 자연수를 리스트로 입력받습니다.
    numbers = list(map(int, input().split()))

    # 수열을 원형으로 생각하면 문제 풀이가 수월해집니다.
    # 원형 수열의 M번째 인덱스에 있는 값은 M % N 인덱스에 있는 값과 동일
    # (M을 수열의 길이로 나눈 나머지 값)
    answer = numbers[M % N]

    print(f"#{test_case} {answer}")
    # ///////////////////////////////////////////////////////////////////////////////////


```

# 21425. +=
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AZD8K_UayDoDFAVs&categoryId=AZD8K_UayDoDFAVs&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=2&pageSize=10&pageIndex=1)
```python
def swap(x, y):
    return y, x

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    A, B, N = map(int, input().split())
    answer = 0
    while True:
        # 문제를 편하게 풀기 위해서 항상 작은 값이 앞에 오도록 합니다.
        if A > B:
            A, B = swap(A, B)
        # 주어진 연산을 수행 후, 연산 횟수(answer)를 1 증가합니다.
        A += B
        answer += 1
        # A에 저장된 값이 N 초과라면 반복문을 멈춥니다.
        if A > N:
            break
    print(answer)

```

# 5185. [파이썬 S/W 문제해결 구현] 1일차 - 이진수
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTtiyIqd_wDFAVT&categoryId=AWTtiyIqd_wDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=2&pageSize=10&pageIndex=1)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    N, num = map(str, input().split())

    # 받은 문자열을 분석하기 쉽게 하기 위해 list로 변경
    num_list = list(num)
    # 10진수로 변경하기 위한 변수 초기화
    num_dec = 0
    # 자승을 위한 변수
    i = 1

    # 16진수를 10진수로 바꾸는 코드
    for n in num_list:
        if n in 'ABCDEF':
            if n == 'A':
                n = '10'
            if n == 'B':
                n = '11'
            if n == 'C':
                n = '12'
            if n == 'D':
                n = '13'
            if n == 'E':
                n = '14'
            if n == 'F':
                n = '15'
        num_dec += int(n) * (16 ** (len(num) - i))
        i += 1
    
    # 10진수 -> 2진수로 바꾸기
    # 앞에 0b 글자 지우기 위해 slicing 진행 [2:]
    answer = (bin(num_dec))[2:]

    # 2진수의 앞에 '0'을 채우기 위한 과정
    remainder = len(answer) % 4
    prefix = ''
    if remainder != 0:
        for i in range(4 - remainder):
            prefix += '0'
    
    # 최종 답 생성
    answer = prefix + answer

    print(f"#{test_case} {answer}")

```

# 5176. [파이썬 S/W 문제해결 기본] 8일차 - 이진탐색
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTa0jjq4ggDFAVT&categoryId=AWTa0jjq4ggDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    N = int(input())

    tree = [0] * (N + 1) # 1번부터 N번 노드까지 저장할 트리 초기화

    num = 1 # 채워 넣을 숫자 변수
    
    def inorder(node):
        global num
        if node > N:
            return
    
        # 왼쪽 방문
        inorder(node * 2)
        # 현재 노드에 값 채우기
        tree[node] = num
        num += 1
        # 오른쪽 방문
        inorder(node * 2 + 1)

    inorder(1) # 루트부터 중위순회 시작

    answer  = tree[1]
    answer2 = tree[N // 2]

    print(f"#{test_case} {answer} {answer2}")

```

# (문제 템플릿)
[문제 링크]()
```python


```

# (문제 템플릿)
[문제 링크]()
```python


```