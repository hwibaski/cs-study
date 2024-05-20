# 탐색 (2)

## 레드-블랙 트리

- 이진 탐색 트리, 균형 탐색 트리

1. 모든 노드는 레드 또는 블랙
2. 루트 노드와 리프 노드는 검정이다
   - 모든 리프 노드는 NULL 노드다.
3. 빨강 노드의 부모 노드는 항상 검정이다.
   - 빨강 노드가 연달아 나타날 수 없음
4. 임의의 노드로부터 리프 노드까지의 경로상에는 동일한 개수의 검정 노드가 존재한다.
5. 한 노드의 왼족 서브트리에 있는 모든 키 값은 그 노드의 키값보다 작다. (이진 탐색 트리의 성질)
6. 한 노드의 오른쪽 서브트리에 있는 모든 키 값은 그 노드의 키값보다 크다. (이진 탐색 트리의 성질)

![img.png](07_image/img.png)

![img_1.png](07_image/img_1.png)

### 탐색

- 이진 탐색 트리의 탐색 방법과 동일

![img_2.png](07_image/img_2.png)

### 삽입 1

- 탐색을 진행하고 실패한 지점에 노드를 삽입한다.

![img_3.png](07_image/img_3.png)

![img_4.png](07_image/img_4.png)

### 삽입 2

![img_5.png](07_image/img_5.png)
![img_6.png](07_image/img_6.png)
![img_8.png](07_image/img_8.png)
![img_7.png](07_image/img_7.png)
![img_9.png](07_image/img_9.png)
![img_11.png](07_image/img_11.png)
![img_10.png](07_image/img_10.png)
![img_13.png](07_image/img_13.png)
![img_12.png](07_image/img_12.png)

### 삽입 연산을 위한 규칙 

- 빨강 노드가 연달아 나타나는 경우에 적용하는 규칙

1. 부모 노드의 형제 노드가 빨강인 경우
   - 부모 노드, 부모 노드의 형제 노드, 부모 노드의 부모 노드의 색깔을 모두 변경
2. 부모 노드의 형제 노드가 검정이고, 현재 노드의 키값이 부모 노드와 부모 노드의 부모 노드(조부모 노드)의 키값이 사이인 경우
    - 현재 노드와 부모 노드를 회전시킴
3. 부모 노드의 형제노드가 검정이고 현재 노드의 키값보다 부모 노드와 조부모 노드의 키값이 큰 (또는 작은) 경우
   - 부모 노드와 주보무 노드를 회전시키고 색깔을 변경

### 성능과 특징

- 균형 탐색 트리
  - 어떤 두 리프 노드의 레벨 차이가 2배를 넘지 않는 균형 탐색 트리
- 탐색, 삽입, 삭제 연산의 시간 복잡도 -> O(logN)
- 사실상 이진 탐색 트리
  - 탐색 연산은 이진 탐색 트리와 동일
  - 삽입 연산은 회전과 색깔 변경과 같은 추가 연산이 필요

![img_14.png](07_image/img_14.png)

## B-트리

- 균형 탐색 트리, (t는 자연수인 상수)

1. 루트 노드는 1개 이상 2t개 미만의 오름차순으로 정렬된 키를 가짐
2. 루트 노드가 아닌 모든 노드는 (t-1)개 이상 2t개 미만의 오름차순으로 졍려된 키를 가짐
3. 내부 노드는 자신이 가진 키의 개수보다 하나 더 많은 자식 노드를 가짐
4. 각 노드의 한 키의 왼쪽 서브트리에 있는 모든 키 값은 그 키값보다 작음
5. 각 노드의 한 키의 오른쪽 서브트리에 있는 모든 키 값은 그 키값보다 큼
6. 모든 리프 노드의 레빌은 동일함

![img_16.png](07_image/img_16.png)

### 탐색

![img_17.png](07_image/img_17.png)

### 삽입

- 루트 노드에서부터 탐색을 수행하여 리프 노드에도 존재하지 않으면 해당 노드에 추가
- 노드 분할
  - 탐색 과정에서 (2t-1)개의 키를 갖는 노드를 만나면, 이 노드를 (t-1)개의 키를 갖는 2개의 노드와 1개의 키를 갖는 노드로 분할
    - 삽입으로 인해 노드의 키의 개수가 2t개가 되는 것을 방지

![img_18.png](07_image/img_18.png)
![img_19.png](07_image/img_19.png)

![img_20.png](07_image/img_20.png)
![img_21.png](07_image/img_21.png)
![img_22.png](07_image/img_22.png)
![img_23.png](07_image/img_23.png)
![img_24.png](07_image/img_24.png)

### 성능과 특징

- 탐색, 삽입, 삭제 연산의 시간 복잡도 -> O(logN)
  - 트리의 높이 h, 각 노드에서 키의 위치를 찾는 시간 O(t) -> O(th)
    - 각 노드 -> 키의 개수 : (t -1) ~ (2t - 1)개, 자식 노드의 개수: t ~ 2t개
    - 모든 리프 노드의 레벨은 동일

![img_25.png](07_image/img_25.png)

![img_26.png](07_image/img_26.png)

## 해시 테이블

- 키 값을 기반으로 데이터의 저장 위치를 직접 계산함으로써 상수 시간 내에 데이터를 저장, 삭제, 탐색할 수 있는 방법

![img_27.png](07_image/img_27.png)
![img_28.png](07_image/img_28.png)
![img_29.png](07_image/img_29.png)

### 해시 함수 - 제산 잔여법

![img_30.png](07_image/img_30.png)

### 해시 함수 - 비닝

![img_31.png](07_image/img_31.png)

### 해시함수 - 중간 제곱법

![img_33.png](07_image/img_33.png)

### 해시 함수 - 문자열을 위한 비닝

![img_32.png](07_image/img_32.png)

### 해시 함수 - 문자열을 위한 단순합

![img_34.png](07_image/img_34.png)

### 해시 함수 - 문자열을 위한 가중 합

![img_35.png](07_image/img_35.png)

### 충돌 해결 방법

![img_36.png](07_image/img_36.png)

### 개방 해싱

![img_37.png](07_image/img_37.png)
![img_38.png](07_image/img_38.png)

### 폐쇄 해싱 - 버킷 해싱

![img_39.png](07_image/img_39.png)
![img_40.png](07_image/img_40.png)
![img_41.png](07_image/img_41.png)
![img_42.png](07_image/img_42.png)
![img_44.png](07_image/img_44.png)

### 폐쇄 해싱 - 선형 탐사

![img_45.png](07_image/img_45.png)
![img_46.png](07_image/img_46.png)
![img_47.png](07_image/img_47.png)
![img_48.png](07_image/img_48.png)
![img_49.png](07_image/img_49.png)
![img_50.png](07_image/img_50.png)
![img_51.png](07_image/img_51.png)
![img_52.png](07_image/img_52.png)
![img_53.png](07_image/img_53.png)
![img_54.png](07_image/img_54.png)
![img_55.png](07_image/img_55.png)
![img_56.png](07_image/img_56.png)

### 폐쇄 해싱 - 이차 탐사

![img_57.png](07_image/img_57.png)
![img_58.png](07_image/img_58.png)
![img_59.png](07_image/img_59.png)
![img_60.png](07_image/img_60.png)
![img_61.png](07_image/img_61.png)

### 폐쇄 해싱 - 이중 해싱

![img_62.png](07_image/img_62.png)

### 삭제 연산

![img_63.png](07_image/img_63.png)

