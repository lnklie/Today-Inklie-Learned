Quaternion.Euler에 대하여
=====
설명
----
- Z축과 X축이 한축으로 합쳐지면서 한축에 대한 계산이 불가능해짐
- 이것을 짐벌락 현상
- 오일러 앵글이 자체적으로 설정되어 있는 순서로 해당 축들을 개별적으로 계산
- 설명 출처 : https://hub1234.tistory.com/21




GPT쌤의 설명
----
- 해당 함수는 x, y, z 축을 기준으로 회전각을 입력받아 쿼터니언 값을 반환
- 입력받는 회전각은 degree 단위로 지정!