동적 계획법(Dynamic Programming)에 대하여
=============
- 특정 범위까지의 값을 구하기 위해 그것과 다른 범위까지의 값을 이용하여 효율적으로 값을 구하는 알고리즘 설계 기법
- 답의 재활용
- 기억하며 풀기라고도 함

구현
------
- 분할 정복 알고리즘과 비슷
- 주어진 문제를 부분 문제로 나누어 각 부분 문제의 답을 계산하고, 이 계산한 결과값을 이용해 원래 문제의 답을 산출
- 분할 정복 알고리즘과 차이점은 나누는 방식
- 최적 부분 구조를 지닌 중복된 하위 문제들을 분할 정복으로 풀이하는 문제해결 패러다임

### 분할 정복 알고리즘

### 최적 부분 구조

접근
--------
- 중복되는 부분 문제(두 번이상 계산되는 부분 문제)에 대한 답을 미리 계산해놓고 연산

조건
------
1. Overlapping Subproblems(겹치는 부분 문제)
- 동일한 작은 문제들이 반복하여 나타나는 경우에 사용이 가능
2. Optimal Substructure(최적 부분 구조)
- 부분 문제의 최적 결과 값을 사용해 전체 문제의 최적 결과를 낼 수 있는 경우

사용
--------
1. DP로 풀 수 있는 문제인지 확인
- 조건 충족 확인
2. 문제의 변수 파악
- 문제 내 변수의 개수를 알아내야 함
3. 변수 간 관계식 만들기(점화식)
4. 메모하기(Memoization or tabulation)
- 변수의 값에 따른 결과를 저장
5. 기저 상태 파악하기
- 가장 작은 문제의 상태를 알아야 함
6. 구현하기
- Bottom-Up(Tabulation 방식) - 반복분
- Top-Down(Memorization 방식) - 재귀 사용

예시
------
- 피보나치 수열

### 재귀 함수 형태의 피보나치 수열
> f(0) = 1 <br>
f(1) = 1<br>
f(n) = f(n-1) + f(n-2) when n > 1
- 이런 재귀 함수의 형태

``` c
int f(unsigned int n)
{
    if(n <= 1)
        return 1;
    else
        return f(n-1)+f(n-2);
}
```
- 숫자가 커지면 시간 복잡도와 공간 복잡도가 지수 스케일로 폭발함(Exponential Explosion)

### 동적 계획법 형태의 피보나치 수열
- 반복 계산을 막기 위해 계산했던 값들을 배열에 저장
- 대표적인 방법이 Top-down과 Bottom-up
#### Top-Down 방식
- Top-down은 위에서 내려오는 것으로 큰 문제부터 시작해서 계속 작은 문제로 분할해 가면서 품
``` c
int memo[100]{}; //메모이제이션 공간. 전역 변수이므로 0으로 초기화
int fibonacci(unsigned int n)
{
  if (n<=1) //0번째, 1번째 피보나치 수
    return n;
  if (memo[n]!=0) //메모가 있는지 확인(0으로 초기화되었으므로 0이 아니라면 메모가 쓰인 것임)
    return memo[n]; //메모 리턴
  memo[n]=fibonacci(n-1) + fibonacci(n-2); //작은 문제로 분할
  return memo[n];
}
```
### Bottom-up 방식
- Bottom-up은 바닥에서 올라오는 것으로. 즉, 작은 문제부터 시작해서 작은 문제를 점점 쌓아 큰 문제를 푸는 것
``` c
int memo[100]{}; //메모이제이션 공간. 전역 변수이므로 0으로 초기화
int fibonacci(unsigned int n)
{
  if (n<=1) //0번째, 1번째 피보나치 수
    return n;
  if (memo[n]!=0) //메모가 있는지 확인(0으로 초기화되었으므로 0이 아니라면 메모가 쓰인 것임)
    return memo[n]; //메모 리턴
  memo[n]=fibonacci(n-1) + fibonacci(n-2); //작은 문제로 분할
  return memo[n];
}
```

참고 자료
---------
https://hongjw1938.tistory.com/47     
https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95#fn-3