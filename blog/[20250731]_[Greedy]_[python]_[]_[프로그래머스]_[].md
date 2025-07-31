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