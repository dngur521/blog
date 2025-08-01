# 체육복
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42862)
```python
def solution(n, lost, reserve):
    # lost와 reserve에 모두 있는 학생은 남에게 못빌려줌 → 둘 다에서 제거
    lost_set = sorted((set(lost) - set(reserve)))
    reserve_set = sorted((set(reserve) - set(lost)))

    # 남은 lost 학생 중에서 앞 번호(i - 1) or 뒷 번호(i + 1)에 여벌이 있는지 확인하고 빌리기 (set에서 제거)
    for i in reserve_set:
        if (i - 1) in lost_set:
            lost_set.remove(i - 1) # 앞 번호에게 빌려주기
        elif (i + 1) in lost_set:
            lost_set.remove(i + 1) # 뒷 번호에게 빌려주기
    
    # 최종 체육수업 들을 수 있는 학생 수 = 전체 학생 수 - 체육복 못 빌린 학생 수
    answer = n - len(lost_set)

    return answer

# print(solution(5, [2, 4], [1, 3, 5]))
# print(solution(5, [2, 4], [3]))
# print(solution(3, [3], [1]))
```

# 조이스틱
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42860)
```python
def solution(name):
    # 1. 위/아래 조작 횟수 중 더 짧은 거리 선택 (char - A, Z - char의 유니코드 값 차이)
    updown_moves = 0
    for char in name:
        updown_moves += min(ord(char) - ord('A'), ord('Z') - ord(char) + 1)

    # 2. 좌/우 조작 횟수 
    n = len(name)
    leftright_moves = n - 1 # 오른쪽으로만 이동하는 경우의 좌/우 조작 수

    # 만약에 이름의 중간에 'A'가 많이 포함되어있는 경우에는 
    # 커서의 양 옆 이동방향을 바꿔 반대편으로 돌아가는것이 더 이득임
    # e.g, "JANAAAAZ" 같은 경우, 뒤쪽 'A'들을 피하기 위해 커서를 되돌아가는 경우가 더 이득임
    for char in range(n):
        next_char = char + 1
        # 연속된 'A'를 만나는 지점 찾기
        while next_char < n and name[next_char] == 'A':
            next_char += 1
        
        # 오른쪽으로 갔다가 왼쪽으로 되돌아오는 경우
        moves = char + char + (n - next_char)
        leftright_moves = min(leftright_moves, moves)

        # 왼쪽으로 갔다가 오른쪽으로 돌아오는 경우도 같이 고려 (대칭)
        moves = (n - next_char) * 2 + char
        leftright_moves = min(leftright_moves, moves)

    answer = updown_moves + leftright_moves
    return answer

# print(solution("JEROEN"))
# print(solution("JAN"))

```

# 큰 수 만들기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42883)
```python

```

# 구명보트
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42885)
```python

```

# 섬 연결하기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42861)
```python

```

# 단속카메라
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42884)
```python

```