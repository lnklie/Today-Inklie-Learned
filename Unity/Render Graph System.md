Render Graph System에 대해 알아보자
==============
- Unity의 Scriptable Render Pipeline(SRP) 위에 있는 시스템
- SRP를 유지, 보수하거나 개별적인 방법으로 커스텀할 수 있도록 하는 것이다.
- HDRP가 이 Render Graph System을 사용함
<br><br>
- render graph를 만들기 위해 RenderGraph API를 사용할 수 있음
- render graph는 리소스를 사용할 때 명퀘하게 상태를 보여주는 커스텀 SRP의 Render 통로?를 고차원으로 보여준다. 
<br><br>
- render pipeline 배치를 간단하게 하고 런타임 퍼포먼스를 상향시켜주는 파이프라인의 다양한 부분들을 효율적으로 관리해주는 이점을가지고 있음

Scriptable Render Pipleline(SRP)란?
--------------