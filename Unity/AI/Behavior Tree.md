Behavior Tree
======
- 행동 트리는 컴퓨터 과학이나 게임에서 사용되는 수학적 모델
- 행동을 트리 구조로 기술
- 한 덩어리의 테스크가 서브트리를 이루게 된다.
- 모듈 식 방식으로 유한한 행동들간의 전환을 나타냄
- 유한상태기계와 비슷하지만 상태가 아닌 작업이라는 차이점이 존재
- 구성 요소: root 노드, control flow 노드, execlution 노드(리프 노드)
- 노드는 깊이 우선 탐색
- 탐색 결과로 자식 노드에서 부모 노드로 상태가 반환됨(Success, Failure, Running)

Control flow 노드
---
- 그 노드 아래에 있는 서브 트리(브랜치)를 통해 표현되는 행동(서브 테스크)을 제어하는 것

Selector
---
- 자식 노드 가운데 하나를 실행하기 위한 노드
- selector의 자식 노드를 왼쪽에서 오른쪽의 순서(우선도가 높은 쪽에서 낮은 쪽)로 깊이 우선 탐색
- Selector의 자식 노드중 하나가 success나 running을 반환하면, selector는 즉시 success나 running을 부모 노드에 반환
- Selector의 모든 자식 노드가 failure를 반환했을 때는 selector도 부모 노드에 failure를 반환

Sequence
---
- 자식 노드를 순서대로 실행하기 위한 노드
- 평가를 시작하면 sequence의 자식 노드를 왼쪽에서 오른쪽의 순서로 깊이 우선 탐색 방식으로 평가
- Sequence의 자식 노드 중 하나가 failure나 running을 반환하면 selector는 즉시 failure나 running을 부모 노드에 반환
- Selector의 모든 자식 노드가 success를 반환했을 때는 selector도 부모 노드에 success를 반환

Composite
---
- 위 두 노드(Selector, Sequence)는 공통적으로 브랜치의 root가 됨
- 디자인 패턴의 composite 패턴과 같은 동작을 보여줌으로 composite 유형으로 분류될 수 있음

조건식
---

### while(Conditional Loop)
- 조건 충족을 평가하는 함수가 true를 반환하는 한, 자식 노드의 평가를 반복
- 조건 충족을 나타내는 함수가 failure를 반환하면 while도 부모 노드에 failure를 반환

### if
- 조건 충족을 평가하는 함수가 true를 반환한 경우, 현재 유효한 자식 노드를 호출해서 그 결과를 반환
- 그 밖의 경우에는 자식 노드 호출 없이 부모 노드에 failure를 반환

### Repeat(Loop)
- 미리 설정해 둔 횟수만큼 자식 노드 평가가 완료되었다면 부모 노드에 success를 반환
- 그 밖의 경우에는 부모 노드에 running을 반환

Execution 노드
---
- 액션이라고도 함
- 리프노드로 작성되며 Behavior Tree 외부에 구현된 구체적인 함수를 호출
- 이 함수의 반환값에 따라 실행 결과의 상태를 판단하여 그 반환 값을 부모 노드에 반환





출처
----
https://engineering.linecorp.com/ko/blog/behavior-tree/
