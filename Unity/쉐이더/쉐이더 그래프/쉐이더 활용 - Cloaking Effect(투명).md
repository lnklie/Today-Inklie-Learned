Clocking Effect(투명) 만들기!
======
- 이번에는 Unlit Shader(빛 연산을 하지 않는 셰이더)로 진행


![Clocking Effect](https://postfiles.pstatic.net/MjAyMjA3MjRfMTA4/MDAxNjU4NjQ4MTY0Mzcw.2YdmClnhoKy9Zzs3HBwvJVNeIRHPEx9xvnQcStgCyqsg.9PEdSKBA2gxsgdwWMdqs7ncIlvV4w1uTk68QvP61JQ8g.GIF.rnlgus1126/Cloaking_Effect.gif?type=w773)

- 이렇게 투명 효과가 나타남.

![Reflaction](https://postfiles.pstatic.net/MjAyMjA3MjRfMjcw/MDAxNjU4NjQ3MjA2OTk1.qUNX177RaLkgqs8doctCRlNN6ix0I_v8DJ7WLbI_xEEg.x7Ztic4jF5ranLs-vswiEVeyMnOxZIyFB3tpXmzdWOEg.PNG.rnlgus1126/Cloaking_Refraction.png?type=w773)

- 모든 Opaque 오브젝트들이 그려진 뒤 해당 오브젝트가 그려지도록 Render Queue를 Transparent로 함
- Scene Color를 그대로 입혀주기 때문에 투명상태
- 픽셀의 Veiw Sapce Normal값을 다른 위치로 지정해줘 적용

### 실루엣을 만들 때는 Fresnel Node 사용
![Fresnel Node](https://postfiles.pstatic.net/MjAyMjA3MjRfMTkw/MDAxNjU4NjQ4NDIzOTcw.rg6_pbqZTsttMb4RPqw_D5adRh9VvnOOArmHaEQLqbIg.cu1JGkS907vyDcE7tiF0NqVCHKArZZm1Eh0TD-KQfaMg.PNG.rnlgus1126/image.png?type=w773)
> 노말맵을 사용하여 디테일을 살리기<br>
(Lit Shader는 Normal Map을 잘 적용 시켜주지만 Unlit은 직접 Normal Map을 적용시켜줘야함 )
### Normal Map
![Normal Map](https://postfiles.pstatic.net/MjAyMjA3MjRfMjE5/MDAxNjU4NjQ4MjE2MTY2.FO7VFbcFggPz18Is9p_T6nI3i1wA2E-0ito6zrmiu1og.ynXf2hzIeuw0rWBkr_z4N0RFMGtzGoI0JPATeKenAVQg.PNG.rnlgus1126/image.png?type=w773)
- 노말맵을 적용 시키면 오브젝트의 굴곡이 살아남
- Normal Map에는 Texture의 픽셀 하나하나 Normal을 나타냄
- 노말맵의 각각의 Vector값을 행렬로 만들어 적용

> 오브젝트에 Normal Map을 적용시킬 때
각 오브젝트는 Bitangent Vector, Normal Vecter, Tangent Vecter가 존재하여
해당 맵들을 오브젝트에 적용해 입히는 것!<br><br>
노말맵을 적용할 때는 Texture2D의 모드를 Bump로<br><br>
C#스크립트에서는 열기준 행렬<br><br>
행기준 일때는 Vector x Matrix

참고 영상
--------
https://youtu.be/M7ICBYmZkds