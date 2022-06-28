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
- 메소드가 대리자를 매개 변수로 허용하고 나중에 대리자를 호출할 수 있음
- 비동기 콜백이라는 방식
- 긴 프로세스 완료 시 호출자에게 알림을 제공하는 일반적인 방법
- 대리자를 사용하는 코드가 사용 중인 메소드의 구현을 확인하지 않아도 됨
- 캡슐화 인터페이스에서 제공하는 기능과 비슷
<br/><br/>
- 콜백은 사용자 지정 비교 메소드를 정의하고 해당 대리자를 정렬 메소드로 전달할 때도 일반적으로 사용
```cs
public static void MethodWithCallback(int param1, int param2, Del Callback)
{
    callback("the number is: " + (param1 + param2).ToString());
}
```
- 메서드로 전달  가능
```cs
MethodWithCallback(1, 2, handler);
```
- 대리자를 추상화로 사용하는 경우 <span style="color:red">MethodWithCallback</span>이 콘솔을 직접 호출할 필요가 없고
- 콘솔을 호출하기 위해 이 메소드를 지정하지 않아도 됨
- <span style="color:red">MethodWithCallback</span>은 단순히 문자열을 준비하여 다른 메소드로 전달할 뿐
- 위임된 메소드는 매개 변수를 필요한 수만큼 사용할 수 있음
<br/><br/>
- 인스턴스 메소드를 래핑하기 위한 대리자를 생성할 때 대리자는 인스턴스와 메소드 모두 참조
- 대리자는 래핑 대상 메소드 이외의 인스턴스 형식은 알 수 없으므로
- 해당 개체에 대리자 서명과 일치하는 메소드가 있으면 모든 개체 형식을 참조할 수 있음
- 정적 메소드를 래핑하기 위해 생성하는 대리자는 메소드만 참조
```cs
public class MethodClass
{
    public void Method1(string message){ }
    public void Method2(string message){ }
}
```
- 대리자는 호출 시 둘 이상의 메소드를 호출할 수 있음, 이러한 호출을 멀티캐스트
- 메소드를 더 추가하려는 경우 더하기 또는 더하기 대입 연산자 사용
```cs
var obj = new MethodClass();
Del d1 = obj.Method1;
Del d2 = obj.Method2;
Del d3 = DelegateMethod;

Del allMethodsDelegate = d1 + d2;
allMethodsDelegate += d3;
```
- <span style="color:red">allMethodsDelegate</span>에는 3개의 메소드 모두 포함
- 순서대로 호출
- 도중 예외가 나온다면 뒤에 나올 메소드도 호출되지 않음
- 반환 값 및/또는 out 매개 변수를 포함하는 대리자는 마지막으로 호출한 메소드의 반환 값과 매개 변수를 반환
- 호출 목록에서 메소드 제거할 때는 빼기 or 빼기 대입 연산자 사용
<br/><br/>
- 대리자 형식은 <span style="color:red">System.Delegate</span>에서 파생되므로
- 해당 클래스로 정의되는 메소드와 속성을 대리자에서 호출 가능
```cs
// 대리자의 호출 목록의 메소드수 확인
int invocationCount = d1.GetInvocationList().GetLength(0);
```
- 멀티 캐스트 대리자는 이벤트 처리에서 사용
- 이벤트 소스 개체는 해당 이벤트를 받도록 등록된 받는 사람 개체에 이벤트 알림을 보냄
- 이벤트를 등록하기 위해 받는 사람은 이벤트를 처리하도록 설계된 메소드를 만든 다음
- 해당 메소드의 대리자를 만들어 이벤트 소스로 전달
- 소스는 이벤트 발생 시 대리자를 호출
- 대리자가 받는 사람에 대해 이벤트 처리 메소드를 호출하여 이벤트 데이터를 전달
- 지전된 이벤트의 대리자 형식은 이벤트 소스에 의해 정의
<br/><br/>
- 컴파일 시간에 할당된 서로 다른 형식의 두 대리자를 비교하면 컴파일 오류가 발생
- 대리자 인스턴스가 정적 <span style="color:red">System.Delegate</span> 형식이면 비교는 허용되지만 런타임에서 false 반환
```cs
delegate void Delegate();
delegate void Delegate2();

static void method(Delegate1 d, Delegate2 e, System.Delegate f)
{
    // 에러
    // Comsole.WriteLine(d == e);

    // 컴파일은 되지만 런다임에서 false가 반환되는 것
    Console.WriteLine(d == f);
}
```
<br/><br/>

명명된 메소드 와 무명 메소드
-------------------
- 대리자는 명명된 메소드에 연결될 수 있음
- 명명된 메소드를 사용하여 대리자를 인스턴스화하면 메소드가 매개 변수로 전달
```cs
// 대리자의 선언
delegate void Del(int x);

// 명명된 메소드 정의
void DoWork(int k){ ... };

// 매개변수로 메소드 사용하는 대리자 인스턴스화
Del d = obj.DoWork;
```
- 명명된 메소드를 사용하여 생성된 대리자는 정적 메소드 또는 인스턴스 메소드를 캡슐화할 수 있음
- 새 메소드 생성이 불필요한 오버헤드인 경우 C#에서 대리자를 인스턴스화하고 호출 시 대리자에서 처리할 코드 블록을 즉시 지정할 수 있음
- 블록에는 람다 식 또는 무명 메소드가 포함될 수 있음
<br/><br/>
- 대리자 매개 변수로 전달하는 메소드에는 대리자 선언과 동일한 시그니처가 있어야 함
- 대리자 인스턴스는 정적 또는 인스턴스 메소드를 캡슐화할 수 있음
>       대리자는 out 매개 변수를 사용할 수 있지만, 멀티캐스트 이벤트 대리자의 경우
>       호출될 대리자를 알 수 없기 때문에 사용하지 않는 것이 좋음

- C#10부터, 하나의 오버로드가 있는 메소드 그룹은 '자연 형식'을 가짐
- 컴파일러는 대리자 형식의 반환 형식과 매개 변수 형식을 유추할 수 있음

### 대리자 사용예제
```cs
// 대리자의 선언
delegate void Del(int i, double j);

class MathClass
{
    static void Main()
    {
        MathClass m =new MathClass();

        // "MultiplyNumbers"메소드를 사용하여 대리자 객체화
        Del d = m.MultiplyNumbers;

        // 대리자 오브젝트 호출
        Console.WriteLine("MultiplyNumbers메소드를 사용한 대리자의 호출: ");
        for(int i = 0; i <= 5; i++)
        {
            d(i,2);
        }

        Console.WriteLine("Press any key to exit.");
        Console.ReadyKey();
    }

    void MultiplyNumbers(int m, double n)
    {
        Console.Write(m * n + " ");
    }
}
``` 
``` cs
delegate void Del();

class SampleClass
{
    public void InstanceMethod()
    {
        Console.WriteLine("A message from ths instance method");
    }

    static public void StaticMethod()
    {
        Console.WriteLine("A message from the static method");
    }
}

class TestSampleClass
{
    static void Main()
    {
        var sc = new SampleClass();

        Del d = sc.InstanceMethod;
        d();

        d = SampleClass.StaticMethod;
        d();
    }
}
```
유니티에서 대리자 사용
--------
- 사운드 처럼 광범위하게 사용하는 메소드가 있다면 대리자에 연결하여 사용할 수 있음

참고자료
----------
https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/delegates/    
https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/delegates/using-delegates    
https://geojun.tistory.com/64 - 유니티에서 대리자 사용