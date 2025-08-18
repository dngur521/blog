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
    # 1. 위/아래 조작 횟수 중 더 짧은 거리 선택 (char ~ A, Z ~ char의 유니코드 값 차이)
    updown_moves = 0
    for char in name:
        updown_moves += min(ord(char) - ord('A'), ord('Z') - ord(char) + 1)

    # 2. 좌/우 조작 횟수 중 더 짧은 거리 선택
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
    # 전체 횟수 = 위/아래 조작 횟수 + 좌/우 조작 횟수
    answer = updown_moves + leftright_moves
    return answer

# print(solution("JEROEN"))
# print(solution("JAN"))

```

# 큰 수 만들기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42883)
```python
def solution(number, k):
    # 문자열 number를 정수 리스트로 변환
    num_arr = [int(n) for n in number]
    stack = []

    # 숫자를 앞에서부터 하나씩 탐색
    for digit in num_arr:
        # 스택의 마지막 숫자보다 현재 숫자가 크면 pop()으로 제거 (k번 까지만 가능)
        while k > 0 and stack and stack[-1] < digit:
            stack.pop()
            k -= 1 # k = k - 1
        stack.append(digit) # 현재 숫자를 스택에 추가

    # 만약 아직 제거하지 못한 k가 남아 있다면, 스택의 뒤에서 그만큼 제거
    if k > 0: 
        stack = stack[:-k]

    # 정수 리스트를 문자열로 변환하여 반환
    answer = ''.join(map(str, stack))
    return answer

# print(solution("1924", 2))
# print(solution("1231234", 3))
# print(solution("4177252841", 4))

```

# 구명보트
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42885)
```python
def solution(people, limit):
    people.sort() # 몸무게 오름차순 정렬
    # 양쪽 끝을 가리키는 두 포인터 사용 
    # (left: 가장 가벼운 사람, right: 가장 무거운 사람)
    left = 0
    right = len(people) - 1
    answer = 0
    # 두 포인터의 위치가 교차되면 종료
    while left <= right:
        # 만약 가벼운 사람과 무거운 사람의 몸무게의 합이 limit 이하면 둘 다 태움
        # → 포인터 둘 다 이동
        if people[left] + people[right] <= limit:
            left += 1
            right -= 1
        # 두 사람의 합이 limit 초과하면 무거운 사람만 태움
        # → right 포인터만 이동
        else:
            right -= 1
        # 한 번 진행할 때 마다 보트 하나 사용
        answer += 1
    return answer

# print(solution([70, 50, 80, 50], 100))
# print(solution([70, 80, 50], 100))


```

# 섬 연결하기
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42861)
```python
# 부모 노드(대표 노드) 찾는 함수
def find(parent, x):
    if parent[x] != x:
        # 경로 압축
        # (찾는 도중 만나는 노드들도 직접 부모와 연결시키기)
        parent[x] = find(parent, parent[x])
    return parent[x]

# 두 노드를 합치는 함수
def union(parent, a, b):
    root_a = find(parent, a)
    root_b = find(parent, b)
    if root_a != root_b:
        # 한 쪽 루트를 다른 쪽 루트에 붙이기
        parent[root_b] = root_a 

def solution(n, costs):
    # 간선을 비용 기준으로 오름차순 정렬
    costs.sort(key=lambda x: x[2])

    # 초기 부모 설정 
    # 초기에는 모든 섬이 자기 자신을 부모로 가짐
    parent = []
    for i in range(n):
        parent.append(i)

    answer = 0     # 최종 최소 비용
    edges_used = 0 # 현재까지 선택한 간선(다리)의 갯수

    for a, b, cost in costs:
        # 각 노드의 root 찾기
        # (두 섬의 대표 부모 노드 찾기)
        root_a = find(parent, a)
        root_b = find(parent, b)

        # 각 노드의 root가 다르면
        # (== 서로 다른 집합이면) 두 노드를 연결하고,
        if root_a != root_b:
            union(parent, a, b)
            # 비용 및 선택한 간선 갯수 추가
            answer += cost  
            edges_used += 1

            # 모든 섬이 연결된 경우 더 이상 진행할 필요가 없으므로 for문 탈출
            if edges_used == n-1:
                break

    return answer
```

# 단속카메라
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42884)
```python
def solution(routes):  
    answer = 0
    #  a > b 인 경우 큰 값이 뒤에 오게 하기
    routes = [(min(a, b), max(a, b)) for a, b in routes]

    # 각 차랑의 경로를 진출 지점 기준으로 오름차순 정렬
    routes.sort(key=lambda x:x[1])

    # 제일 먼저 끝나는 구간의 끝 지점에 카메라를 두기
    # (for문에서 초기화 할 수 있으니 마이너스 무한대로 먼저 초기화)
    cam_now = -float('inf')

    # 이후 순서대로 보면서 
    # 현재 카메라 위치가 다음 구간의 진입 지점보다 작으면
    # == 그 구간을 못 찍으면
    # 그 구간의 진출 지점에 새 카메라 두기
    for start, end in routes:
        if cam_now < start:
            cam_now = end
            answer += 1
    
    return answer

# print(solution([[-20,-15], [-14,-5], [-18,-13], [-5,-3]]))

```