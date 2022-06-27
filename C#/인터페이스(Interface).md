인터페이스(Interface)에 대하여
===============
- 클래스와 비슷하게 인터페이스는 메소드, 속성, 이벤트, 인덱서를 가짐
- 하지만 이를 직접 구현하지 않고 단지 정의만을 가짐
- 추상 멤버로만 구성된 추상 Base클래스와 개념적으로 유사
- 클래스가 인터페이스를 가지는 경우 해당 인터페이스의 모든 멤버와 대한 구현을 제공
<br/><br/>
- 한 클래스는 하나의 Base클래스만을 가질 수 있지만, 인터페이스는 여러 개를 가질 수 있음
- 예제
``` cs
public class MyConnection : Compenent, IDbConnection, IDisposable
{
    // 인터페이스 IDbConnection, IDisposable 구현
}
```
<br/><br/>
- 클래스뿐만 아니라 구조체와 인터페이스도 인터페이스를 상속 가능
<br/><br/>
! 수정으로 바꾸면 안되는 경우 !
1. 상속하려는 인터페이스가 소스 코드가 아닌 어셈블리로만 제공되는 경우
2. 상속하려는 인터페이스의 소스 코드를 갖고 있어도 이미 인터페이스를 상속하는 클래스들이 존재하는 경우 

인터페이스의 장점
-------
- 클래스는 여러 클래스를 한꺼번에 상속하면 죽음의 다이아몬드 문제가 발생할 수 있음
- 인터페이스는 내용이 아닌 외형을 물려주기 때문에 발생하지 않음
- 여러 인터페이스를 다중 상속하는 클래스를 상속해보자~

인터페이스 정의
------- 
- C#키워드 interface를 사용하여 정의
- 인터페이스 정의 시에는 내부 멤버들에 대해 public과 같은 접근 제한자를 사용하지 않음
- 모든 것이 public
- 예제
``` cs
public interface IComparable
{
    int CompareTo(object obj);
}
```

인터페이스 구현
-------
- 인터페이스를 가질 경우 인터페이스의 모든 멤버에 대한 구현을 해야함
- 메소드들은 public 한정자로 수식해야함
- 인터페이스를 인스턴스화 할 수 없음, new를 사용하여 객체를 생성할 수 없음
- 참조는 만들 수 있음, 참조에 파생 클래스의 위치를 담는 것

```cs
public class MyClass : IComparable
{
    private int key;
    private int value;

    public int CompareTo(object obj)
    {
        MyClass target = (MyClass)obj;
        return this.key.CompareTo(target.key);
    }
}
```


인터페이스 사용
-------
- 클래스와 인테페이스의 정의는 객체지향 프로그래밍으로 디자인하고 구현하는데 가장 중요한 핵심
- 상속받는 클래스의 인스턴스는 만들 수 있음


```cs
interface ILogger
{
    void WriteLog(string message);
}

class ConsoleLogger : ILogger
{
    public void WriteLog(string message)
    {
        Console.WriteLine("{0} {1}", DataTime.Now.ToLocalTime(), message);
    }
}

class FileLogger : ILogger
{
    private StreamWriter writer;

    public FileLogger(string path)
    {
        writer = File.CreateText(path);
        writer.AutoFlush = true;
    }
    public void WriteLog(string message)
    {
        writer.WriteLine("{0} {1}", DateTime.Now.ToShortTimeString(), message);
    }
}

class ClimateMonitor
{
    private ILogger logger;
    // 요렇게 참조할 수 있는 변수는 만들 수 있다~
    public ClimateMonitor(ILogger logger)
    {
        this.logger = logger;
    }

    public void start()
    {
        while(true)
        {
            Console.Write("온도를 입력하셈 : ");
            string temperature = Console.ReadLine();
            if(temperature == "") break;

            logger.WriteLog("현재온도 : " + temperature);
        }
    }
}

class MainApp
{
    static void Main(string[] args)
    {
        ClimateMonitor monitor = new ClimateMonitor(new FileLogger("MyLog.txt"));

        monitor.start();
    }
}
```
<br/><br/>
- 예제 2 
``` cs
public void Run()
{
    IDbConnection dbCon = GetDbConnection();
    dbCon.Open();
    if(dbCon.State == ConnectionState.Open)
    {
        dbCon.Close();
    }
}

public IDbConnection GetDbConnection()
{
    IDbConnection dbConn = null;
    string cn = ConfigurationManager.AppSettings["Connection"];
    switch(ConfigureationManager.AppSettings["DbType"])
    {
        case "SQLServer":
            dbConn = new SqlConnection(cn);
            break;
        case "Oracle":
            deConn = new OracleConnection(cn);
            break;
        case "OleDb":
            dbConn = new OleDbConnection(cn);
            break;
    }
    return dbConn;
}
```
<br/><br/>
- 예제 3 
- 인터페이스가 인터페이스를 상속하는 경우
```cs
interface ILogger
{
    void WriteLog(string message);
}

interface IFormattableLogger : ILogger
{
    void writeLog(string format, params Object[] args);
}

class ConsoleLogger2 : IFormattableLogger
{
    public void WriteLog(string message)
    {
        Console.WriteLine("{0} {1}", DataTime.Now.ToLocalTime(), message);
    }
    public void WriteLog(string format, params Object[] args)
    {
        String message = String.Format(format, args);
        Console.WriteLine("{0} {1}", DataTime.Now.ToLocalTime(), message);
    }
}

class MainApp
{
    static void Main(string[] args)
    {
        IFormattableLogger logger = new ConsoleLogger2();
        logger.WriteLog("The world is not flat");
        logger.WriteLog("{0} + {1} = {2}", 1, 1, 2);
    }
}
```


참고자료
-------
https://www.csharpstudy.com/CSharp/CSharp-interface.aspx    
https://blog.naver.com/rnlgus1126/222523327920    
