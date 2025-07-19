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
def solution(n, computers):
    visited = [False] * n # 각 노드의 방문 여부 저장하는 리스트
    count = 0 # 연결된 네트워크 갯수

    def DFS(node):
        # 현재 노드를 방문했음
        visited[node] = True
        # 컴퓨터(노드)의 갯수만큼 반복 (모든 노드 검사)
        for j in range(n):
            # 연결 정보에서 현재 노드와 j가 연결되어있고 j를 아직 방문 하지 않았으면 
            # j 노드에 대해 DFS 재귀호출 
            if computers[node][j] == 1 and not visited[j]:
                DFS(j)

    # 컴퓨터(노드)의 갯수만큼 반복 (모든 노드 검사)
    for i in range(n):
        # 방문하지 않은 노드면
        if visited[i] == False:
            # 해당 노드로부터 연결된 모든 컴퓨터 탐색(깊이 우선 탐색 사용)
            DFS(i)
            # 하나의 네트워크를 찾았으므로 count 증가
            count += 1

    return count

# print(solution(3, [[1, 1, 0], [1, 1, 0], [0, 0, 1]]))
# print(solution(3, [[1, 1, 0], [1, 1, 1], [0, 1, 1]]))
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