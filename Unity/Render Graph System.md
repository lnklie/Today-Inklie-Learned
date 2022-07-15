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

### Scriptable Render Pipleline(SRP)란?
- 기존에 엔진에 묶여있던 Render Pipeline 제어를 C#을 통해 직접 제어할 수 있는 것

Render Graph System의 이점
----------

### 메모리 관리의 효율성
- 자원 할당을 수동으로 관리 할때 동시에 매 렌더링 특성이 활성화 될 때마다 처리하고 최악의 시나리오에 할당해줘야한다. 특정한 렌더링 특성이 활성화되지 않을 때 해당 기능을 처리하는 리소스가 있지만 Render Pipeline은 그들을 사용하지 않게 한다. 반대로 Render Graph는 실제로 사용하는 리소스만 할당하게 해줌

### 자동적인 동기화 지점을 생성
- 비동기 계산 큐는 일반 그래픽 워크로드와 병렬로 실행될 수 있으므로 Render Pipeline을 처리하는데 걸리는 전체 GPU시간이 줄어들 수 있음 하지만 비동기 계산 큐와 일반 그래픽 큐 간의 동기화 지점을 정의 및 유지 관리하기 어렵지만 자동으로 해줌

### 유지 관리
- Render Graph는 리소스를 내부적으로 관리하여 Render Pipeline을 쉽게 유지 관리 할 수 있음

참고자료
------
https://docs.unity3d.com/Packages/com.unity.render-pipelines.core@10.2/manual/render-graph-system.html
https://mathmakeworld.tistory.com/55