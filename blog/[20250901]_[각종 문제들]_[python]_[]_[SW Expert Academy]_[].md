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

# 4828. [파이썬 S/W 문제해결 기본] 1일차 - min max
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTLQZwKon4DFAVT&categoryId=AWTLQZwKon4DFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=3)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    n = int(input())
    list = input().split()

    # 숫자들을 list로 입력받은 후 int로 형변환
    N = [int(item) for item in list]

    # 오름차순으로 정렬
    N.sort()

    # 가장 큰 수와 가장 작은 수의 차이 구하기
    answer = N[-1] - N[0]

    print(f"#{test_case} {answer}")

```

# 4834. [파이썬 S/W 문제해결 기본] 1일차 - 숫자 카드
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTLVouKpUgDFAVT&categoryId=AWTLVouKpUgDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=3)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    n = int(input())
    nums = input()
    
    # 각 숫자의 갯수를 저장할 딕셔너리 생성
    card_count = {}

    # 각 숫자마다 순회
    for i in range(n):
        # 현재 숫자가 딕셔너리의 key로 이미 존재한다면
        if(nums[i] in card_count):
            # 그 숫자(key)의 값을 1 증가
            card_count[nums[i]] += 1
        # 현재 숫자가 딕셔너리의 key로 아직 존재하지 않는다면
        else:
            # 새로운 key - value 쌍을 딕셔너리에 추가(초기화)
            card_count[nums[i]] = 1
    
    # max() 함수와 lambda식 활용해서 
    # 가장 많은 카드의 숫자(key)와 장 수(value) 얻기
    max_item = max(card_count.items(), key=lambda item: (item[1], item[0]))
    answer1 = max_item[0]
    answer2 = max_item[1]

    print(f"#{test_case} {answer1} {answer2}")

```

# 4835. [파이썬 S/W 문제해결 기본] 1일차 - 구간합
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTLXCuapdcDFAVT&categoryId=AWTLXCuapdcDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=3)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # N: 정수의 갯수, M: 구간의 갯수
    N, M = map(int, input().split())

    # int형 요소들이 있는 list 입력받기
    nums = input().split()
    nums = [int(item) for item in nums]
    
    # 쓰일 변수들 초기화
    sum     = 0  # 각 계산마다의 합
    sums    = [] # 각 계산마다의 합을 저장할 list
    min_sum = 0  # M개의 합이 가장 큰 경우
    max_sum = 0  # M개의 합이 가장 작은 경우
    answer  = 0  # 정답

    # list를 M개의 구간마다 순회하면서 각각의 합을 저장 
    for i in range(0, N - M + 1):
        for j in range(i, i + M):
            sum += nums[j]
        sums.append(sum)
        sum = 0

    # 합의 가장 큰 경우와 작은 경우 저장
    min_sum = min(sums)
    max_sum = max(sums)

    # 정답 계산
    answer = max_sum - min_sum
    print(f"#{test_case} {answer}")

```

# 4836. [파이썬 S/W 문제해결 기본] 2일차 - 색칠하기
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTLZMRKpsYDFAVT&categoryId=AWTLZMRKpsYDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=3&&&&&&&&&&)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # 10 * 10 격자 초기화
    grid = [[0]*10 for _ in range(10)]

    # N: 칠할 영역의 갯수
    N = int(input())
    for _ in range(N):
        answer = 0
        # r1, c1: 왼쪽 위 모서리 인덱스, r2, c2: 오른쪽 아래 모서리, 
        # color: 색상 정보(1: 빨강, 2: 파랑)
        r1, c1, r2, c2, color = map(int, input().split())
        
        # 각 영역마다 주어진 색으로 칠하기(누적합)
        for i in range(r1, r2 + 1):
            for j in range(c1, c2 + 1):
                grid[i][j] += color
        
        # 10 * 10 격자를 전부 순회하면서 
        # 영역의 값이 3(1+2;보라색)인 부분 체크
        for i in range(10):
            for j in range(10):
                if grid[i][j] == 3:
                    answer += 1
    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4839. [파이썬 S/W 문제해결 기본] 2일차 - 이진탐색
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTLcyA6qAMDFAVT&categoryId=AWTLcyA6qAMDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):

    p, p_a, p_b = map(int, input().split())
    l_a, l_b = 1, 1
    r_a, r_b = p, p
    c_a, c_b = 0, 0
    count_a, count_b = 0, 0
    
    while (c_a != p_a):
        c_a = int((l_a + r_a) // 2)
        if c_a < p_a:
            l_a = c_a
        elif c_a > p_a:
            r_a = c_a
        count_a += 1

    while (c_b != p_b):
        c_b = int((l_b + r_b) // 2)
        if c_b < p_b:
            l_b = c_b
        elif c_b > p_b:
            r_b = c_b
        count_b += 1

    if count_a < count_b:
        answer = "A"
    elif count_a > count_b:
        answer = "B"
    else:
        answer = "0"

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4861. [파이썬 S/W 문제해결 기본] 3일차 - 회문
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQQXcKQHkDFAVT&categoryId=AWTQQXcKQHkDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    N, M = map(int, input().split())
    board = []
    answer = ""
    for _ in range(N):
        board.append(input())

    # 가로방향 회문 검사
    for row in range(N):
        # 0 ~ M, 1 ~ M + 1, ... 식으로 부분 인덱스 구해서 문자열 추출
        for start in range(N - M + 1):
            sub_str = board[row][start : start + M]

            # 회문 검사
            # [::-1]는 list 슬라이싱을 통해 문자열을 뒤집는것
            if sub_str == sub_str[::-1]:
                answer = sub_str
                break
        if answer:
            break
        # 답이 나왔을 경우 더 이상 탐색하지 않고 바로 종료

    # 세로방향 회문 검사 (가로방향에서 찾지 못한 경우)
    if not answer:
        for col in range(N):
            # 하나의 세로줄을 문자열로 만들기
            col_str = ""
            for row in range(N):
                col_str += board[row][col]
            
            # 만들어진 세로줄에서 부분 문자열 추출
            for start in range(N - M + 1):
                sub_str = col_str[start : start + M]
                
                # 회문 검사
                if sub_str == sub_str[::-1]:
                    answer = sub_str
                    break
            if answer:
                break

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# (문제 템플릿)
[문제 링크]()
```python


```

# (문제 템플릿)
[문제 링크]()
```python


```

# (문제 템플릿)
[문제 링크]()
```python


```