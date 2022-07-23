아우라 만들기!
======
- Edit -> RenderPipeline -> Universal Render Pipeline에서 Standard Material일 경우 URP전용 Material로 업그레이드가능
- 직접 Material 인스펙터 창에서도 Shader를 Universal Render Pipeline으로 설정 가능

![Kyle Effect](https://postfiles.pstatic.net/MjAyMjA3MjJfMjA5/MDAxNjU4NDg3MDExMDY4.Ru7miDxjjMq5nCvr2yHH8lTnsMlgDHmSSBIgS4WqiBAg.8Ps-DSROyPw9KFUcKG2ck6UMtsh2sHv9vXOjdH3QU80g.GIF.rnlgus1126/Kyle_Effect.gif?type=w773)
- 이렇게 겉에 빨간색으로 스킨이 입혀지는 효과


### Position Vertex
![Position Vertex](https://postfiles.pstatic.net/MjAyMjA3MjJfMTEw/MDAxNjU4NDg3MDY1NzE5.u0-RYjzLuXRn7ZBMFMqfYKAhiYx7Jdu8QTvFid2JLCwg.9HeYHlxUqzvkRfjso6czZt-D2GEU_Kf9taApuR2PWGYg.PNG.rnlgus1126/Kyle_Effect_Position.png?type=w773)
- Normal Vector와 수치를 곱한 값과 위치를 더해 
- Vertex(정점) 위치에 넣는다.
- 모든 정점을 조금 씩 위로 올리는 느낌

### Color Fragment
![Color Fragment](https://postfiles.pstatic.net/MjAyMjA3MjJfNzUg/MDAxNjU4NDg3MTQ1NTYz.F-EcnUPQLBtx8DVxqqjg3JuGDF3JnIiZD-6zU0oGc6gg.ynjIOn-FXrK6SAnx0RcTBQfli7KKV-ncI_8JgDTDaLgg.PNG.rnlgus1126/Kyle_Effect_Color.png?type=w773)
1. Fresnel Effect를 사용하여 오브젝트의 가장자리에 반사만 되도록 함
여기서 좀 더 강하게 Power(제곱)하고
Color(색)을 입힌다(Multiply).

2. UV를 시간(Time)에 따라 나타나도록 더하고(Add) Texture하나를 넣고 Sample Texture 2D하나를 만듬

- ​(1), (2)에서 만들어진 노드를 곱해서(Multiply)해서 Color에 연결한다.

 
> 이것을 Kyle Effect라고 하나보다.

​

### 프레넬 효과(Fresnel Effect)
https://docs.unity3d.com/kr/current/Manual/StandardShaderFresnel.html

참고 영상
--------
https://youtu.be/VvK7sLbbLYE