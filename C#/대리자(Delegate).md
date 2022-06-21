대리자(Delegate)에 대하여
=============
- 대리자는 특정 매개 변수 목록 및 반환 형식이 있는 메서드에 대한 참조를 나타내는 형식
- 대리자를 인스턴스화하면 모든 메서드가 있는 인스턴스를 호환되는 시그니터 및 반환 형식에 연결 가능
- 대리자 인스턴스를 통해 메서드를 호출
- 대리자는 메서드를 다른 메서드에 인수로 전달되는데 사용
- 이벤트 처리기는 대리자를 통해 호출되는 메소드라고 할 수 있음
- 액세스 사능한 클래스 또한 대리자 형식과 일치하는 구조의 모든 메소드는 대리자에 할당할 수 있음

대리자의 사용
--------
- 대리자는 C나 C++의 함수 포인터처럼 메소드를 안전하게 캡슐화하는 방식
- 개체 지향적이고 형식이 안전하고 보안이 유지

- 예제
```cs
public delegate void Del(string message);
```  
- 대리자 개체는 일반적으로 대리자가 래핑할 메소드의 이름을 제공하거나 람다식을 사용하여 생성
- 호출자가 대리자에게 전달한 매개 변수가 메소드로 전달되며 메소드가 반환 값이 호출자로 반환
- 이 과정을 대리자 호출

```cs
// 대리자를 위한 메소드 생성
public static void DelegateMethod(string message)
{
    Console.WriteLine(message);
}
```
```cs
// 대리자 생성
Del handler = DelegateMethod;

// 대리자 호출
handler("Hello World");
```
- 대리자 형식은 .NET의 Delegate 클래스에서 파생되며 봉인되어 있기에
- Delegeate에서는 파생될 수 없고 해당 클래스에서 지정 클래스를 파생할 수도 없음
- 인스턴스화된 대리자는 개체이므로 인수로 전달하거나 속성에 할당할 수 있음


참고자료
----------
https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/delegates/    
https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/delegates/using-delegates