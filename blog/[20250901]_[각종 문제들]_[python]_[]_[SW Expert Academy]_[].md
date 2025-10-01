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

# 4864. [파이썬 S/W 문제해결 기본] 3일차 - 문자열 비교
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQRytKQJ0DFAVT&categoryId=AWTQRytKQJ0DFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2&&&&&&&&&&)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    
    # 각각의 문자열을 입력받고, 각 문자열의 길이 저장
    str1 = input()
    str2 = input()
    str1_len = len(str1)
    str2_len = len(str2)

    answer = 0

    # 윈도우 슬라이딩 기법으로 str2의 부분 문자열과 str1 비교
    for i in range(str2_len - str1_len + 1):
        if str2[i : i + str1_len] == str1:
            # 부분 문자열이 같으면 answer는 1
            answer = 1

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4865. [파이썬 S/W 문제해결 기본] 3일차 - 글자수
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQSs6qQL0DFAVT&categoryId=AWTQSs6qQL0DFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    
    # 각각의 문자열을 입력받기
    str1 = input()
    str2 = input()
    # str1의 각 문자를 key로 가지고 값이 0인 딕셔너리 초기화
    str1_dict = {char: 0 for char in str1}
    answer = 0

    # 딕셔너리의 각 키 값과 str2의 각 문자르르 비교
    for key in str1_dict:
        for char in str2:
            # 키와 문자가 같으면 그 키의 value 1 증가
            if key == char:
                str1_dict[key] += 1

    # 딕셔너리의 value 값 중에서 최대값 뽑아내기
    answer = max(list(str1_dict.values()))

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4873. [파이썬 S/W 문제해결 기본] 4일차 - 반복문자 지우기
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQbpTaQfEDFAVT&categoryId=AWTQbpTaQfEDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    
    # 문자열 입력받기
    str = input()
    # 빈 스택 초기화
    stack = []

    # 문자열의 각 문자 차례대로 순회
    for char in str:
        # 스택이 비어있거나 현재 문자가 스택의 최상위 문자랑 다르다면
        # 스택에 현재 문자 추가
        if len(stack) == 0 or char != stack[-1]:
            stack.append(char)

        # 현재 문자와 스택의 최상위 문자가 같다면
        # 스택의 최상위 문자 pop
        elif char == stack[-1]:
            stack.pop()

    # 정답은 스택의 길이와 동일(== 남겨진 문자열의 길이)
    answer = len(stack)

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4874. [파이썬 S/W 문제해결 기본] 5일차 - Forth
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQc1MKQiIDFAVT&categoryId=AWTQc1MKQiIDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    error_flag = False
    answer = 0
    # 후위 연산식 list로 입력받기
    str_list = input().split()

    # 빈 스택 초기화
    stack = []

    # 연산식의 연산자 하나씩 순회
    for oper in str_list:
        # 연산자가 .이면 연산이 끝났다는 의미이므로 break
        if oper == '.':
            break
        # 연산자가 숫자(==피연산자)면 stack에 추가
        if oper.isdigit():
            stack.append(int(oper))
        # 연산자가 연산자일때의 각각 처리 (+, -, *, /)
        elif oper in '+-*/':
            # 연산을 하려는데 stack에 있는 숫자가 2개 미만이면
            # 제대로 된 식이 아니므로
            # error 플래그를 True로 설정하고 break
            if len(stack) < 2:
                error_flag = True
                break
            # 피연산자 2개 스택에서 pop 해서 
            # 실제 연산 처리
            oper2 = stack.pop()
            oper1 = stack.pop()

            if oper == '+':
                stack.append(oper1 + oper2)
            elif oper == '-':
                stack.append(oper1 - oper2)
            elif oper == '*':
                stack.append(oper1 * oper2)
            elif oper == '/':
                stack.append(oper1 // oper2)

    # 순회를 다 돌고 난 다음에 혹시 있을 예외 상황 처리
    # stack의 길이가 1 이상이면 정상적인 식이 아님
    # or
    # stack의 길이가 1이지만 입력받은 식의 맨 끝 글자가 '.'이 아니면 정상적인 식이 아님
    if len(stack) > 1 or (len(stack) == 1 and str_list[-1] != '.'):
        error_flag = True

    # 최종 정답 출력
    if not error_flag and len(stack) == 1:
        answer = stack[0]
        print(f"#{test_case} {answer}")
    else:
        # error_flag가 True인 경우 error 출력
        print(f"#{test_case} error")

```

# 4875. [파이썬 S/W 문제해결 기본] 5일차 - 미로
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQeET6QlADFAVT&categoryId=AWTQeET6QlADFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=2&&&&&&&&&&)
```python
def dfs(x, y):
    # 상하좌우 4가지 방향으로 이동하는 좌표 표현할때 쓸 list
    # 예: (dx[3], dy[3]) = (0, 1) ==> 오른쪽으로 이동
    # 즉 (x + dx[i], y + dy[i]) 처럼 이동하는 새로운 위치를 계산하기 유용함
    dx = [-1, 1, 0, 0]
    dy = [0, 0, -1, 1]

    # 방문한 위치 표시
    visited[x][y] = True

    # 상, 하, 좌, 우로 이동
    for dr in range(4):
        nx = x + dx[dr]
        ny = y + dy[dr]
        # 이동할 때 미로 범위 벗어나지 않도록 조건 설정
        if 0 <= nx < N and 0 <= ny < N and not visited[nx][ny]:
            # 이동한 위치가 0(==통로)이면 dfs 재귀호출
            if arr[nx][ny] == 0:
                dfs(nx, ny)
            # 이동한 위치가 3(==도착)이면 1 반환
            elif arr[nx][ny] == 3:
                global answer
                answer = 1
            # 이동한 위치가 1인 경우는 처리 안함

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    global visited, N, arr
    answer = 0
    x = 0
    y = 0
    # 미로의 크기 N 입력받기
    N = int(input())
    # 미로의 통로와 벽에 대한 정보 입력받기
    # 0은 통로, 1은 벽, 2는 출발, 3은 도착
    arr = [list(map(int, input().strip())) for _ in range(N)]

    # 먼저 미로에서 출발점(숫자 2)의 위치 찾아서 출발 좌표 설정
    for i in range(N):
        for j in range(N):
            if arr[i][j] == 2:
                x = i
                y = j
    
    # dfs에서 사용할 visited list 초기화 (N*N 크기)
    visited = [[False] * N for _ in range(N)]

    # 출발 좌표에서 dfs 함수 호출
    dfs(x, y)
    
    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 4880. [파이썬 S/W 문제해결 기본] 5일차 - 토너먼트 카드게임
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQgnH6Qq4DFAVT&categoryId=AWTQgnH6Qq4DFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1)
```python
def find_winner(start, end, arr):
    # 그룹에 학생이 한 명 뿐이라면, 그 학생이 해당 그룹의 승자가 됨
    # 따라서 그 학생의 번호 반환
    if start == end:
        return start
    
    # 이분탐색을 위한 인덱스 설정 및 재귀호출
    mid = (start + end) // 2
    left_winner  = find_winner(start,   mid, arr)
    right_winner = find_winner(mid + 1, end, arr)
    
    # 무승부일 경우 번호가 작은쪽(인덱스가 작은 쪽)을 승자로 함
    if arr[left_winner] == arr[right_winner]:
        return left_winner
    # 가위(1)는 보(3)을 이김
    if arr[left_winner] == 1 and arr[right_winner] == 3:
        return left_winner
    elif arr[left_winner] == 3 and arr[right_winner] == 1:
        return right_winner
    
    # 바위(2)는 가위(1)를 이김
    elif arr[left_winner] == 2 and arr[right_winner] == 1:
        return left_winner
    elif arr[left_winner] == 1 and arr[right_winner] == 2:
        return right_winner
    
    # 보(3)는 바위(2)를 이김
    elif arr[left_winner] == 3 and arr[right_winner] == 2:
        return left_winner
    elif arr[left_winner] == 2 and arr[right_winner] == 3:
        return right_winner
    
    else:
        return 0

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    answer = 0
    # 인원 수 N 입력받기
    N = int(input())

    global arr
    # N명이 고른 카드 입력받기
    arr = list(map(int, input().split()))

    # 정답 찾기
    answer = find_winner(0, N - 1, arr)

    # 정답 출력
    print(f"#{test_case} {answer + 1}")

```

# 4881. [파이썬 S/W 문제해결 기본] 5일차 - 배열 최소 합
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTQh00qQs0DFAVT&categoryId=AWTQh00qQs0DFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1&&&&&&&&&&)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    answer = 0
    # N 및 N*N list 입력받기
    N = int(input())
    arr = []
    for _ in range(N):
        arr.append(list(map(int, input().split())))

    min_sum = float('inf') # 최솟값을 찾기 위해 무한대로 초기화

    # 백트래킹 사용
    def find_min_sum(row, current_sum, used_cols):
        global min_sum

        # 현재까지의 합이 이미 최소 합보다 크거나 같으면 더 탐색할 필요 없음
        # (가지치기)
        if current_sum >= min_sum :
            return
        
        # 모든 행을 다 탐색했으면 최솟값 갱신
        if row == N:
            min_sum = min(min_sum, current_sum)
            return
        
        # 현재 행에서 각 열을 순회하며 숫자 선택
        for col in range(N):
            # 이전에 사용되지 않은 열인지 확인
            if col not in used_cols:
                # 사용된 열에 현재 열 추가
                used_cols.add(col)
                # 다음 행으로 재귀 호출
                find_min_sum(row + 1, current_sum + arr[row][col], used_cols)
                # 백트래킹: 다음 탐색을 위해 사용된 열에서 현재 열 제거
                used_cols.remove(col)

    # 함수 호출
    find_min_sum(0, 0, set())
        
    # 정답 출력
    print(f"#{test_case} {min_sum}")

```

# 5102. [파이썬 S/W 문제해결 기본] 6일차 - 노드의 거리
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTVmxDKb1oDFAVT&categoryId=AWTVmxDKb1oDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1)
```python
from collections import deque

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    answer = 0
    # V개의 노드 개수와 방향성이 없는 E개의 간선 정보 입력 받기
    V, E = map(int, input().split())

    # V+1 크기의 리스트 graph 만들기
    graph = [[] for _ in range(V + 1)]

    # E개의 줄에 걸쳐, 간선의 양쪽 노드 번호가 주어짐
    for _ in range(E):
        a, b = map(int, input().split())
        # 입력받은 그래프 정보 저장하기
        # 방향성이 없는 그래프이므로 양쪽 모두에 추가해주기
        graph[a].append(b)
        graph[b].append(a)

    # E개의 줄 이후에는 출발 노드 S와 도착 노드 G가 주어짐
    S, G = map(int, input().split())

    # 큐 생성: 앞으로 방문할 노드들을 순서대로 저장하는 공간
    queue = deque()

    # 거리 배열 초기화: 출발 노드 S로부터 다른 모든 노드까지의 거리를 저장할 배열임
    # -1은 아직 업데이트가 안된 초기값이라는 뜻
    # e.g, distance[2] ==> 노드 S에서 노드 2까지의 거리
    distance = [-1 for _ in range(V+1)]
    # S에서 S까지의 거리는 0 (자기 자신)
    distance[S] = 0

    # BFS로 출발 노드 S에서 도착 노드 G까지의 최단 거리 계산

    # 큐에 시작 노드 S 삽입
    queue.append(S)
    
    # 큐가 비어있을 때까지 반복
    while(queue):
        # 큐에서 노드 하나 꺼내기
        current_node = queue.popleft()

        # 현재 노드가 도착 노드 G라면 distance[G]가 바로 정답. (탐색 종료)
        if current_node == G:
            answer = distance[G]
            break
        
        # 현재 노드와 연결된 모든 이웃노드들 가져오기
        neighboor_node = graph[current_node]
        for node in neighboor_node:
            # 만약 이웃 노드들을 아직 방문하지 않았다면
            # 출발 노드 S에서 이웃 노드까지의 거리 업데이트 (현재 노드의 거리에서 1 더한 값)
            if distance[node] == -1:
                distance[node] = distance[current_node] + 1
                # 거리가 업데이트 된 이웃 노드들을 큐에 추가 (다음에 탐색할 노드 추가)
                queue.append(node)
            # 이미 방문한 이웃 노드들은 위의 로직으로 거리가 업데이트가 되었기 때문에 따로 탐색 X
    
    # 만약 반복문이 끝났는데도 출발 노드 S에서 노드 G까지의 거리가 업데이트 되지 않았다면
    # S에서 G로 가는 경로가 없다는 것임.
    if distance[G] == -1:
        answer = 0
    
    # 정답 출력
    print(f"#{test_case} {answer}")


```

# 5177. [파이썬 S/W 문제해결 기본] 8일차 - 이진 힙
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTa1f7q4kIDFAVT&categoryId=AWTa1f7q4kIDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1)
```python
# 부모 노드: (i / 2)에 바닥 함수 적용
# 왼쪽 자식: 2i
# 오른쪽 자식: 2i + 1

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    answer = 0
    tree = [0] # 인덱스 번호를 1번부터 맞추기 위한 dummy값 초기화

    # N: 입력받을 자연수의 갯수
    N = int(input())

    # N개의 자연수 입력받기
    nums = list(map(int, input().split()))

    for i in range(N):
        # 새로운 값을 리스트의 맨 끝에 추가하기
        tree.append(nums[i])
        index = i + 1

        # 맨 처음 삽입한 노드가 아닌경우
        while index > 1:

            # 현재 노드의 값과 부모 노드의 값 비교
            # 만약 새 노드의 값이 부모 노드의 값보다 작다면,
            # 두 노드의 값을 swap
            # 이 과정을 노드가 root에 도달하거나 부모보다 값이 더 이상 작지 않을 때까지 반복
            if tree[index] < tree[index//2] and not index == 1:
                tree[index], tree[index//2] = tree[index//2], tree[index] 
                # 교환 후, 인덱스는 부모 노드의 인덱스로 업데이트
                index = index//2
            else:
                break
    # print(tree)

    # 마지막 노드의 조상 노드들에 저장된 정수의 합을 알아내기
    last_node = tree[-1]
    index = N
    while index > 1:
        answer += tree[index//2]
        index = index//2

    # 정답 출력
    print(f"#{test_case} {answer}")

```

# 5174. [파이썬 S/W 문제해결 기본] 8일차 - subtree
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AWTay1Z64cQDFAVT&categoryId=AWTay1Z64cQDFAVT&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=1)
```python
def count_nodes(adj, curr):
    # 현재 노드 자신을 카운트
    count = 1

    # 자신의 자식들에 대해서 순회
    # 리스트가 비어있다면 반복문이 실행되지 않으므로
    # 별도의 if문 필요 없음.
    for child_node in adj[curr]:

        # 재귀 호출: 자식 노드가 루트인 서브트리의 갯수 계산
        count_from_child_subtree = count_nodes(adj, child_node)

        # 자식 서브트리의 갯수를 누적해서 더하기
        count += count_from_child_subtree

    # 최종 서브트리의 갯수 반환
    return count

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # E: 간선의 갯수, N: 루트가 될 노드
    E, N = map(int, input().split())

    # E개의 부모 자식 노드 번호 쌍 입력받기 
    nums = list(map(int, input().split()))

    # 인접 리스트 초기화
    adj = [[] for _ in range(E + 2)]

    # 인접 리스트에 트리 구조 구축
    for i in range(0, E * 2, 2):
        # 부모(p) - 자식(c) 쌍 인덱스
        p = nums[i]
        c = nums[i+1]
        adj[p].append(c)

    # 노드 N에 대해서 자식 노드들의 갯수 세기
    answer = count_nodes(adj, N)

    # 정답 출력
    print(f"#{test_case} {answer}")


```

# 1204. [S/W 문제해결 기본] 1일차 - 최빈수 구하기
[문제 링크](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=2&contestProbId=AV13zo1KAAACFAYh&categoryId=AV13zo1KAAACFAYh&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=2&pageSize=10&pageIndex=5)
```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # 테스트 케이스의 번호
    t = int(input())

    # 점수들 입력받기
    nums = list(map(int, input().split()))

    # 딕셔너리 초기화
    num_dict = {}

    # 점수들을 key로 하고 각 점수들의 등장 횟수를 value로 하는 딕셔너리 생성
    for num in nums:
        if num in num_dict:
            num_dict[num] += 1
        else:
            num_dict[num] = 1
    
    # 빈도수(value) 내림차순, 만약에 빈도수가 같을 시 점수(key) 내림차순 정렬
    temp = sorted(num_dict.items(), key=lambda item: (item[1], item[0]), reverse=True)

    # 최종 정답은 첫번째 튜플의 점수(key)임
    answer = temp[0][0]
    
    # 정답 출력
    print(f"#{test_case} {answer}")


```

# (문제 템플릿)
[문제 링크]()
```python


```