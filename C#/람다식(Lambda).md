람다식(Lambda)
=========
- 익명 메소드를 지칭하는 용어
- 간결한 방법으로 함수를 묘사하기 위함
- 모든 것이 함수로 이루어져 있음
- 람다 선언 연산자 =>를 사용하여 람다의 매개 변수 목록을 구분

```cs
(input-parameters) => expression
```
```cs
(Input-parameters) => { <sequence-of-statements> }
```

- 람다 식을 만들려면 람다 연산자 왼쪽에 입력 매개 변수를 지정하고 다른 쪽에 식이나 문 블록을 지정
- 대리자 형식으로 변환이 가능
- 람다 식을 변환할 수 있는 대리자 형식은 해당 매개 변수 및 반환 값의 형식에 따라 정의
- 람다 식에서 값을 반환하지 않는 경우 <span style="color:red">Action</span>대리자 형식 중 하나로 변환 가능
- 값을 반환하는 경우는 <span style="color:red">Func</span>대리자로 변환할 수 있음
```cs
Func<int, int> square = x => x * x;
Console.WriteLine(squre(5));
// 결과
// 25

// 식트리 형식
System.Linq.Expression<Func<int, int>> e = x => x * x;
Console.WriteLine(e);
// 결과
// x => (x * x)
```
- 대리자 형식이나 식 트리의 인스턴스가 필요한 코드에 람다 식을 백그라운드에서
 실행해야하는 코드를 전달하기위해 Task.Run(Action)메소드의 인수 등으로 사용할 수 있음
```cs
int[] numbers = { 2, 3, 4, 5 };
var squaredNumbers = numbers.Select(x => x * x);
Console.WriteLine(string.Join(" ", squaredNumbers));
// 결과
// 4 9 16 25
```

식 람다
-----
- => 연산자의 오른쪽에 있는 식이 있는 람다식을 식 람다라고 함
```cs
(input-parameters) => expression
```
- 식 람다의 본문은 메서드 호출로 구성될 수 있음
- 하지만 SQL Server에서처럼 .NET CLR(공용 언어 런타임)의 컨텍스트 외부에서 평가되는 식 트리를 만드는 경우에는 람다 식에서 메소드 호출을 사용하면 안됨
- 메소드는 .NET CLR의 컨텍스트 내에서만 의미가 있음

Lambda.Complie 메소드
----
- 식 트리로 기술된 람다식을 실행 코드로 컴파일하고 람다식을 나타내는 대리자를 생성

참고자료
--------
https://docs.microsoft.com/ko-kr/dotnet/csharp/language-reference/operators/lambda-expressions    
https://namu.wiki/w/%EB%9E%8C%EB%8B%A4%EC%8B%9D
