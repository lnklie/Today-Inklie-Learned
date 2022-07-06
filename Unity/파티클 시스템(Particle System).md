파티클 시스템(Particle System)에 대하여
=========
- 씬 안에 다수의 작은 2D이미지를 생성하고 애니메이션에서 액체, 구름 및 불꽃 같은 유체 엔티티를 시뮬레이션함

속성
------

| 이름 | 설명 |
|---|---|
|Duration| 파티클의 지속시간|
|Looping| 반복할지 여부|
|Prewarm| Looping이 체크되어 있을 때 활성화, 파티클이 한 싸이클 동작한 상태에서 실행되는 것|
|Start Delay| Prewarm이 체크 되어 있지 않을 때 활성화, 시작 시간을 지정할 수 있음|
|Start Lifetime| 한 파티클의 재생 시간, 짧을 수록 빨리 없어 진다.|
|Start Speed| 파티클의 속도|
|3D Start Size| 파티클의 크기를 설정 |
|3D Start Rotation| 파티클의 회전 값을 설정 |
|Flip Rotation| 0 ~ 1사이의 값, 파티클을 반대 방향으로 회전시키는 비율을 설정, 시작 회전 값의 반대 부호|
|Start Color| 파티클의 색상 설정 |
|Gravity Modifier| 파티클이 받는 중력 설정 |
|Simulation Space| 파티클의 동작하는 환경을 설정, Local / World / Custom(Transform을 설정) |
|Simulation Speed| 파티클 시스템 자체의 속도를 설정, 파티클의 속도, Duration이 영향을 받음 |
|Delta Time| Time.TimeScale에 영향을 받을지 말지 결정, Unscaled는 받지 않게 된다. |
|Scaling Mode| 파티클의 Scale에 영향을 주는 방법을 설정, Hierarchy를 설정하면 부모 오브젝트의 Scale에 영향을 받게 됨  |
|Play On Awake| 오브젝트 활성화 시 시작할지 여부를 설정 |
|Emitter Velocity| 파티클 시스템의 속도를 계산할 때, Rigidbody / Transform을 사용할 지를 설정 |
|Max Particles| 파티클의 한 싸이클에서 최대 수량을 설정|
|Auto Random Seed| 파티클이 랜덤으로 나오는지 체크, 해제 시 똑같이 나오고 나오는 형식 수를 설정 가능 |
|Stop Action| 파티클이 정지한 후의 행동을 설정 여러가지 상황에서 설정 가능|
|Culling Mode| 파티클 시스템에서 방출한 파티클이 스크린을 벗어나면 취할 행동 설정, <br>Pause - 중단, <br>Pause and Catch-up은 스크린에서 벗어 나면 멈춘 뒤 다시 들어오면 다시 시작, <br>Always Simulate - 항상,<br> Automatic - 반복 설정일 경우 pause / 기타 시스템일 경우 Always |
|Ring Buffer Mode| 파티클이 파티클의 최대 수량에 도달할 때까지 계속 활성화 <br> Disabled - 수명이 경과한 파티클을 제거 <br> Pause Until Replaced - 파티클 일시정지 했다가 재사용<br> Loop Until Replaced - 수명 비율 지점을 설정하여 해당 지점으로 다시 돌아가고 Max에서 재사용|

모듈
-----
### Emission(방출)
- 방출관련

| 이름 | 설명 |
|---|---|
|Rate over Time| 초당 방출하는 파티클 수를 설정 |
|Rate over Distance| 거리당 방출하는 파티클 수 설정 |
|Bursts| 파티클을 한번에 방출 |
|Time| 시작 시간을 설정 |
|Count| 한번에 방출하는 파티클 수 설정  |
|Cycles| Duration, 진행시간동안 몇 번 할지 설정   |
|Interval| 방출 간격 설정  |
|Probability | 방출 확률 설정   |

### Shape(모양)
- 파티클이 퍼지는 모양 관련 설정 혹은 파티클 조각의 모양

| 이름 | 설명 |
|---|---|
|Shape| 퍼지는 모양 설정, 모양에 따라 각도 반지름 등을 설정할 수 있음 |
|Texture| 파티클에 텍스쳐도 입힐 수가 있음 |
|Position, Rotation, Scale| transform요소들도 설정할 수 있음 |
|Align To Direction| 체크가 되어 있으면 퍼지는 방향으로 2D 파티클이 보이고 체크 해제 시에는 카메라 방향으로 보임  |
|Randomize Direction| 방향의 랜덤 확률 정함 |
|Spherize Direction| 퍼지는 방향이 중앙에서 원형 모양으로 퍼짐  |
|Randomize Position| 시작 위치를 랜덤하게 지정가능, 커질수록 랜덤한 위치가 많아짐  |

참고자료
------
https://notyu.tistory.com/59