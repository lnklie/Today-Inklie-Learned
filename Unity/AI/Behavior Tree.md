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