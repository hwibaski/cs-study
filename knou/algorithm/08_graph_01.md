# 그래프 (1)

## 기본 개념

 - G=(V, E)
 - V: 정점(Vertex)의 집합
 - E: 간선(Edge)의 집합

![img_1.png](08_image/img_1.png)

## 그래프 주요 용어

- 인접 정점(Adjacent Vertex): 간선으로 직접 연결된 정점, 두 정점 u, v 사이에 간선이 있으면 u와 v는 인접
- 부수 (incident) : 간선이 정점에 부수되어 있는 것, 해당 간선은 정점 u와 v에 부수되어 있다.
- 경로 (path) : 간선으로 연결된 일련의 정점들의 순서
- 경로의 길이 (length) : 경로를 구성하는 간선의 수
- 차수 (degree) : 해당 정점에 부수된 간선의 수
  - 진입 차수 (in-degree) : 정점으로 들어오는 간선의 수
  - 진출 차수 (out-degree) : 정점에서 나가는 간선의 수
- 단순 경로 (simple path) : 한 경로 상에서 처음과 마지막 정점을 제외한 모든 정점이 서로 다른 경로
- 사이클 (cycle) : 단순 경로의 시작 정점과 종료 정점이 동일한 경우
- 루프 (loop) : 사이클이면서 경로의 길이가 1인 경로
- 연결 (connected) : 무방향 그래프에서 서로 다른 정점의 모든 쌍에 대해 경로가 있으면 연결, 방향 그래프에서는 서로 다른 두 정점의 모든 쌍에 대해서 양방향의 방향경로가 존재하면 그 방향 그래프는 강력 연결되었다고 한다.

## 그래프의 구현 방법

- 인접 행렬 (Adjacency Matrix)
  - 2차원 배열을 사용하여 두 정점을 연결하는 간선의 유무를 표현
- 인접 리스트 (Adjacency List)
  - 연결 리스트를 사용하여 각 정점에 인접한 정점들을 연결하여 표현

![img.png](08_image/img.png)

## 그래프 순회

- 그래프의 모든 정점을 체계적으로 한 번씩 방문하는 것
  - 그래프 탐색 방법

- 순회 방법
  - DFS (Depth First Search) : 깊이 우선 탐색
  - BFS (Breadth First Search) : 너비 우선 탐색

### 탐색 과정에서의 정점의 구분

- 방문 정점 : 방문이 완료된 정점
- 주변 정점 : 방문 정점에 인접한 정점 중에서 아직 방문하지 않은 정점
- 미도달 정점 : 방문 정점도 주변 정점도 아닌 전혀 접근하지 못한 정점
- 깊이 우선 탐색 -> 최근의 주변 정점을 우선 방문
- 너비 우선 탐색 -> 주변 정점 주에서 오래된 것을 우선 방문

![img_2.png](08_image/img_2.png)

### DFS (Depth First Search)

- 한 정점을 시작으로 매번 인접한 정점 중 한 곳으로 이동하며 탐색하는 방법
  - 최근의 주변 정점을 우선으로 방문하는 탐색 방법

- 스택을 이용하여 구현
  - 현재 정점에 인접한 정점이 없어서 더 이상 탐색을 진행할 수 없으면 거꾸로 되돌아가면서 아직 탐색하지 않은 인접한 정점을 찾아서 탐색을 진행

- 처리 과정
  1. 시작 정점을 스택에 삽입
  2. 스택의 top에 있는 정점에 대한 주변 정점이 존재하면 그중 하나의 정점을 스택에 삽입하고 방문한 정점으로 처리. 주변 정점이 없다면 스택의 top에 있는 정점을 제거
  3. 스택에 더 이상의 정점이 없을 때까지 2의 과정을 반복

![img_3.png](08_image/img_3.png)

![img_4.png](08_image/img_4.png)
![img_5.png](08_image/img_5.png)
![img_6.png](08_image/img_6.png)
![img_7.png](08_image/img_7.png)
![img_8.png](08_image/img_8.png)
![img_9.png](08_image/img_9.png)
![img_10.png](08_image/img_10.png)
![img_11.png](08_image/img_11.png)
![img_12.png](08_image/img_12.png)
![img_13.png](08_image/img_13.png)
![img_14.png](08_image/img_14.png)
![img_15.png](08_image/img_15.png)
![img_16.png](08_image/img_16.png)
![img_17.png](08_image/img_17.png)
![img_18.png](08_image/img_18.png)
![img_19.png](08_image/img_19.png)
![img_20.png](08_image/img_20.png)
![img_21.png](08_image/img_21.png)
![img_22.png](08_image/img_22.png)
![img_23.png](08_image/img_23.png)

### DFS 성능과 특징

- 인접 리스트 -> O(정점의 개수 + 간선의 개수)
- 인접 행렬 -> O(정점의 개수^2)
- 재귀로도 가능
![img_24.png](08_image/img_24.png)

### BFS (Breadth First Search)

- 시작 정점을 기준으로 거리가 가장 가깝게 인접한 정점을 우선으로 모두 방문한 후 시작 정점과의 거리가 멀어지는 순서로 인접 정점들을 탐색하는 방법
  - 거리 : 시작 정점으로부터의 경로의 길이
- 주변 정점 중에서 가장 오래된 것부터 우선 방문하는 방법
- 큐를 사용하여 주변 정점을 정리

![img_26.png](08_image/img_26.png)

![img_27.png](08_image/img_27.png)
![img_28.png](08_image/img_28.png)
![img_29.png](08_image/img_29.png)
![img_30.png](08_image/img_30.png)
![img_31.png](08_image/img_31.png)
![img_32.png](08_image/img_32.png)
![img_33.png](08_image/img_33.png)
![img_34.png](08_image/img_34.png)
![img_35.png](08_image/img_35.png)
![img_36.png](08_image/img_36.png)
![img_37.png](08_image/img_37.png)
![img_38.png](08_image/img_38.png)
![img_39.png](08_image/img_39.png)

### BFS 성능과 특징

- 인접 리스트 -> O(정점의 개수 + 간선의 개수)
- 인접 행렬 -> O(정점의 개수^2)

## 그래프 순회의 응용

### 위상 정렬

- 무사이클 방향 그래프에서 모든 간선이 한 방향으로만 향하도록 정점을 한 줄로 나열하는 것

![img_40.png](08_image/img_40.png)

- 깊이 우선 탐색을 활용하여 구함
  - DFS를 수행하다가 더 이상 주변 정점이 없어서 되돌아갈 때, 스택에서 삭제되는 정점을 역순으로 나열하면 됨

![img_41.png](08_image/img_41.png)
![img_42.png](08_image/img_42.png)
![img_43.png](08_image/img_43.png)
![img_44.png](08_image/img_44.png)
![img_45.png](08_image/img_45.png)
![img_46.png](08_image/img_46.png)
![img_47.png](08_image/img_47.png)
![img_48.png](08_image/img_48.png)
![img_49.png](08_image/img_49.png)
![img_50.png](08_image/img_50.png)
![img_51.png](08_image/img_51.png)
![img_52.png](08_image/img_52.png)
![img_53.png](08_image/img_53.png)

![img_54.png](08_image/img_54.png)

### 그래프의 연결성

- 정점 간의 연결 관계를 다루는 것
  - 연결 성분 (connected component)
    - 무방향 그래프에서 임의의 두 정점 간의 경로가 존재하는 최대 부분 그래프
      - 너비 우선 탐색 또는 깊이 우선 탐색을 활용하여 구함
      - ![img_55.png](08_image/img_55.png)
  - 강연결 성분 (strongly connected component)
    - 방향 그래프에서 임의의 두 정점 사이에 양방향의 경로가 존재하는 최대 부분 그래프
      - ![img_56.png](08_image/img_56.png)
      - ![img_57.png](08_image/img_57.png)
      - ![img_58.png](08_image/img_58.png)
        - 모든 간선의 방향을 반대로 뒤집은 그래프 (Gr)
      - ![img_59.png](08_image/img_59.png)
