파티클 시스템(Particle System)에 대하여
=========
- 씬 안에 다수의 작은 2D이미지를 생성하고 애니메이션에서 액체, 구름 및 불꽃 같은 유체 엔티티를 시뮬레이션함

초기 모듈
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

설정 모듈
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

### VelcoCity over Lifetime(속도)

- 속도 조절 및 뻗어나가는 각도 등을 조절 가능
- 회전하는 파티클을 사용할 때 좋음

| 이름 | 설명 |
|---|---|
|Linear| 직선이 뻗어나가는 방향으로 속도를 조절 / X, Y, Z 지정 가능 |
|Orbital X| 궤도를 형성하는 것처럼 X, Y, Z 축으로 파티클을 회전하도록 함 |
|Offset X| 회전시 X, Y, Z 축으로 얼마나 떨어져있는지 설정 |
|Radial| 파티클이 방사하는 방향으로 더 많이 나아가 회전을 더욱 크게 형성|
|Speed Modifier| 속도를 지정 |

### Limit VelcoCity over Lifetime(속도 제한)

- 속도제한을 줄 수 있음
- 제한이 넘는 상황에서도 속도를 지정 가능

| 이름 | 설명 |
|---|---|
|Seperate Axes| 각 축으로 나아가는 파티클의 속도를 제한 / X, Y, Z 지정 가능 |
|Seperate Axes 해제시 Speed| 전체적인 속도 제한 |
|Dampen| 초과 속도가 얼마나 줄어들게 되는지 제어 |
|Drag| 저항값, 시간이 지날수록 점점 Speed를 낮춤 |

### Inherit Velocty(속도 상속)

- 파티클이 부모로부터 상속을 받도록 설정

| 이름 | 설명 |
|---|---|
|Mode| Initial(생성시 한번) / Current(지속적으로 계속 영향) 설정이 가능|
|Multiplier| 속도를 상속받는 비율 |

### Lifetime by Emitter Speed(방사체 속도 수명)

- 방사체의 속도의 전체적인 포물선?을 설정

| 이름 | 설명 |
|---|---|
|Multiplier| 포물선 비율 설정 |
|Speed Range| 속도 범위 설정 |

### Force over Lifetime(파티클에 가하는 힘)

- 파티클에 힘을 가하는 설정 (X, Y, Z축으로 힘을 줄 수 있음)
- 공간(World, Local), 랜덤 지정 가능

### Color over Lifetime
- 지점마다 색깔을 설정 가능

### Color by Speed
- 속도 별 색상도 지정 가능

### Size over Lifetime
- 크기 포물선 지정 가능
- 각각 x, y, z 축 개별적으로도 지정 가능

### Size by Speed
- 속도 별 사이즈 설정
- 각각 개별적으로 지정 가능하고, 속도 범위도 가능

### Rotation over Lifetime
- 파티클 하나 하나의 자체적인 회전 설정, 기본적으로 z축
- 회전속도를 설정 가능 그리고 개별적으로도 가능

### Rotation by Speed
- 속도 별 회전도 가능

### External Forces
- 윈드 존(Wind Zone)에 영향을 받는 정도 설정

### Noise(노이즈 효과)
- 파티클에 노이즈 효과를 주어 불규칙적인 움직임
- 파리나 먼지 혹은 반딧불이처럼 움직임
- Preview로 대강의 모양을 볼 수 있음

| 이름 | 설명 |
|---|---|
|Strength| 강도 설정 |
|Frequency| 노이즈 효과의 빈도를 설정 |
|Scroll Speed| 불규칙한 움직임의 속도 설정 |
|등등|등등|

### Collision(충돌 효과)
- 파티클에 충돌 효과를 줌

| 이름 | 설명 |
|---|---|
|Type| Plane을 만들어 충돌 / World는 모든 콜라이더와 충돌|
|Visualization| 시각화 어떤걸로 할건지 정함 Grid / Solid |
|Scale Plane| Plane 크기 |
|Dampen|파티클 중돌시 그 속도에 대해 속성만큼 비율을 유지, 1이 아니면 파티클은 충돌 후 느려짐|
|Bounce|충돌 후 표면으로부터 팅겨져 나오는 파티클 파편의 속도|
|LifeTime Loss|각 충돌에서 Start Lifetime 손실의 비율, 수명이 0이 되면 파티클이 죽음|
|Min Kill Speed|충돌 이후 파티클이 해당 스피드 아래로 떨어지면 시스템으로부터 제거|
|등등|등등|

### Triggers(트리거 효과)
- 게임 오브젝트와 충돌 판정
- Inside, Outside, Enter, Exit 상황에서 무시하거나 없애거나 콜백할 수 있음

### Sub Emitters(서브 파티클 방출)
- 파티클이 다양한 상황들에서 서브 파티클을 방출

### Texture Sheet Animation
- 텍스쳐, 애니메이션 설정

### Lights(빛 설정)
- 파티클의 빛을 설정, 파티클에 라이트를 추가가능

### Trails(서브 파티클 방출)
- 파티클에 꼬리 선을 추가할 수 있음

### Custom Data(커스텀 데이터)
- 파티클에 연결할 커스텀 데이터 포맷을 에디터에 정의할 수 있음

### Renderer
- 파티클의 이미지나 렌더링을 설정


참고자료
------
https://notyu.tistory.com/59    
https://docs.unity3d.com/kr/2019.4/Manual/ParticleSystemModules.html