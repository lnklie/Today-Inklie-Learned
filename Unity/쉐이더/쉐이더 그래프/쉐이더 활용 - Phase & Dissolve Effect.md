Phase & Dissolve Effect 만들기!
======
- 원리는 alpha Clip을 이용해서 일부 Pixel만 보이고 안 보이고를 조절해서
- Phase & dissolve 효과를 나타냄

![Phase Effect](https://postfiles.pstatic.net/MjAyMjA3MjNfMjMy/MDAxNjU4NTc4NzI4ODAy.ef69uHYE_5e9UkYdjtZhTQsW7YERfnyrPUl88TW5BJ0g.vPJMlwVjmm5oH3LTXwipImibY81LN3l9HcQd5rn1hg8g.GIF.rnlgus1126/Phase_Effect.gif?type=w773)
![Dissolve Effect](https://postfiles.pstatic.net/MjAyMjA3MjNfMjcg/MDAxNjU4NTc4NzM5MzE5.rNSU4sqROAESE7IEBaI5tcaMf7Yabim83MT69fzuQgUg.lc4CADRoI2aCkurv7LPhukKXbcv98R8HBTn3TOZzIMkg.GIF.rnlgus1126/Dissolve_Effect.gif?type=w773)
- 이렇게 SF효과를 낼 수 있다.

### Texture2D 구성하기
![Position Vertex](https://postfiles.pstatic.net/MjAyMjA3MjNfMTky/MDAxNjU4NTc4NzcxMDMz.l8kMSnIKX0yaJqlatkDmFC17ZnTE805UdF7ITnxlwY0g.fgE_hUbmeFf0bDdEu2rUpmAUcivqGyU15se89octm_4g.PNG.rnlgus1126/Phase_Dissolve_Both_Effect.png?type=w773)
- 공통적으로 Texture2D같은 파라미터 들을 만들고 노드식으로 연결시켜
![Color Fragment](https://postfiles.pstatic.net/MjAyMjA3MjNfMzkg/MDAxNjU4NTc4ODcxMjMw.fdx-figzylRijji5Hn5fLvopy8Rju2FnDchhENptLO4g.pj5_Az0nF4RPeqojnOm2Gx-89dpkysz5MwboKuuLQrog.PNG.rnlgus1126/image.png?type=w773)
- 이렇게 Material의  인스펙터 창에 나타낼 수가 있음

### Phase Effect
![Phase Effect](https://postfiles.pstatic.net/MjAyMjA3MjNfNjQg/MDAxNjU4NTc5MDAzNzgy.KexqVd74mNce1G94h-aHVyMdZFRyXRmyAnUgGrMSqJYg.oMWw16Gc3hHP1_F1DCfXEZTztHmv7KwFn-Lhv5r6sSkg.PNG.rnlgus1126/Phase_Effect.png?type=w773)
- 핵심 노드는 Step 노드
- Position을 값을 RGB로 나누어(Split) Y값인 G만 수정하도록 한다.
- 띠를 만들어야하기 때문에 Step 노드는 둘 두개의 부분을 빼고(Subtract) 
- 색깔(Glow Color 프로퍼티)을 곱한뒤(Multiply)
- 위의 Emission Map(빛을 내는 맵)과 더해 Emission에 넣음
- 큰 부분은 Alpa에 넣어  Alpha Clip Threshold 값을 기준으로 점점 나타나도록 한다.

##### Step Node : Edge와 In을 비교 0또는 1로 반환 In이 Edge보다 클 경우 1, Edge가 In보다 클 경우 0
https://docs.unity3d.com/Packages/com.unity.shadergraph@6.9/manual/Step-Node.html

### Dissolve Effect
![Dissolve Effect](https://postfiles.pstatic.net/MjAyMjA3MjNfMjkw/MDAxNjU4NTc5NDY4NjYx.8mNJu0EmJFYX60J1zp6-f3yee9yF9IZkwwfgW78r8pkg.rkKi3NymSja-nqEjO9D_Cph8d2ax7mSNDbSKRcpiB4kg.PNG.rnlgus1126/Dissolve_Effect.png?type=w773)
- Position 말고 NoiseMap을 사용하도록 한다.
- 이것도 두 Step Node를 빼서 노이즈 부분에 띠를 만드는 형식
- 마찬가지로 띠부분을 빛나게 하고 Alpha를 이용해 점점 나타나도록 함

참고 영상
--------
https://youtu.be/1fQzBYepKrY