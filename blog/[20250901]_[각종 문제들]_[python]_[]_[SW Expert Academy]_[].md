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

# (문제 템플릿)
[문제 링크]()
```python


```