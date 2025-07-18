# 타겟 넘버
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43165)
```python
def solution(numbers, target):
    def dfs(index, current_sum):
        # 종료 조건: 모든 숫자를 다 사용했을 때
        if index == len(numbers):
            if current_sum == target:
                return 1 # 정답 1개 찾음
            else:
                return 0
        # 현재 숫자를 + 또는 -로 사용하는 두 갈래 재귀 호출
        plus  = dfs(index + 1, current_sum + numbers[index])
        minus = dfs(index + 1, current_sum - numbers[index])

        # 두 경우에서 얻은 정답 갯수 합산
        return plus + minus

    answer = dfs(0, 0)
    return answer

# print(solution([1, 1, 1, 1, 1], 3))
# print(solution([4, 1, 2, 1], 4))
```

# 네트워크
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43162)
```python

```

# 게임 맵 최단거리
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/1844)
```python

```

# 단어 변
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43163)
```python

```

# 아이템 줍기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/87694)
```python

```

# 여행 경로 
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43164)
```python

```

# 퍼즐 조각 채우기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/84021)
```python

```