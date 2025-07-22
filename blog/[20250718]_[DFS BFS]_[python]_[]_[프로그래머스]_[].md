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
def solution(maps):

    queue = []
    n = len(maps)     # 행 (row)
    m = len(maps[0])  # 열 (col)
    dest = (n-1, m-1) # 목적지 좌표

    # 동, 서, 남, 북 방향 (행, 열 변화량)
    dx = [1, -1, 0, 0]  # 행(row) 변화량
    dy = [0, 0, 1, -1]  # 열(col) 변화량

    # 방문 여부를 저장할 2차원 배열 초기화
    visited = []
    for i in range(n):
        row = []
        for j in range(m):
            row.append(False)
        visited.append(row)
    
    # 시작 위치는 방문 처리 -> True
    visited[0][0] = True
    
    # 큐에 시작 위치와 거리 정보 추가 
    queue.append([0, 0, 1]) # (x, y, 거리)

    # 큐가 빌 때까지 반복 (BFS)
    while queue:
        x, y, dist = queue.pop(0) # 큐에서 pop하기

        # 만약 현재 좌표가 목적지 좌표랑 같다면 거리값 return
        if (x, y) == dest:
            return dist

        # 현재 위치에서 상하좌우 4방향으로 이동
        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]

            # 맵 범위를 벗어나지 않았으면
            if 0 <= nx < n and 0 <= ny < m:
                # 벽이 아니고 (maps[nx][ny] == 1)
                # 아직 방문하지 않았으면
                if maps[nx][ny] == 1 and not visited[nx][ny]:
                    # 방문 표시, 큐에 (nx, ny, dist + 1) 추가
                    visited[nx][ny] = True
                    queue.append((nx, ny, dist + 1))

    # 목적지에 도달하지 못하는 경우 -1 return
    return -1

# print(solution([[1,0,1,1,1],[1,0,1,0,1],[1,0,1,1,1],[1,1,1,0,1],[0,0,0,0,1]]))
# print(solution([[1,0,1,1,1],[1,0,1,0,1],[1,0,1,1,1],[1,1,1,0,0],[0,0,0,0,1]]))

```

# 단어 변환
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43163)
```python
# 두 단어에서 한 글자만 다를 때 True 반환하는 함수
def is_one_diff(word1, word2):
    word1_list = list(word1)
    word2_list = list(word2)
    diff = 0

    for i in range(len(word1_list)):
        if word1_list[i] != word2_list[i]:
            diff += 1
        if diff > 1:
            return False
    return True 

def solution(begin, target, words):

    # target이 words에 없으면 변환 불가능 -> 0 반환
    if target not in words:
        return 0

    # BFS 탐색 준비: 방문 여부 리스트와 큐 초기화
    visited = [False] * len(words)
    queue = [(begin, 0)] # (현재 단어, 변환 횟수)
    count = 0

    while queue:
        # 큐에서 현재 단어와 변환 횟수 꺼내기
        cur_word, count = queue.pop(0)

        # words 목록 중 아직 방문하지 않았고, 
        # 현재 단어와 한 글자만 다른 단어들 모두 찿기 (is_one_diff 함수 사용)
        for i, word in enumerate(words):
            if not visited[i] and is_one_diff(cur_word, word):
                # 그 단어가 target이면 count + 1 반환
                if word == target:
                    return count + 1
                # 그 단어가 target이 아니면 방문 표시하고 큐에 다시 넣기
                visited[i] = True
                queue.append((word, count + 1))
        
    # 큐가 비었는데도 target에 도달하지 못하면 0 반환
    return 0

# print(solution("hit", "cog", ["hot", "dot", "dog", "lot", "log", "cog"]))
# print(solution("hit", "cog", ["hot", "dot", "dog", "lot", "log"]))
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