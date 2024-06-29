SOLID 원칙이란?
-----
- 객체 지향 프로그래밍에서 지켜야할 5가지 원칙
- 코드의 유연성과 유지 보수성을 높이기 위한 방법

### 1. 단일 책임 원칙 (SRP, Single Responsibility Principle)
- 기본적으로 클래스는 하나의 책임을 가져야한다는 것이다.
- 위의 정의는 모호하기에
- 하나의 클래스가 변경되는 이유는 한 가지여야 한다는 것으로 해석하는 것이 좋다.
- 단일 책임 원칙이 잘 지켜진다면 변경사항이 있을 경우 한 가지만 고치면 된다.
- (출처 : https://mangkyu.tistory.com/194)
#### 내가 만들어본 예시 코드 
``` C#
public class UserData
{
    private string nickName = "";
    private int attackPower = 0;
    
    public void SetNickName(string _nickName)
    {
        nickName = _nickName;
    }
    public void SetAttackPower(int _attackPower)
    {
        attackPower = _attackPower;
    }
    public int GetAttackPower()
    {
        return attackPower;
    }
}

public class UserController
{
    public void Attack(int attackPower)
    {
        // 공격
    }
}

public class User
{
    private UserData userData = null;
    private UserController userController = null;

    public void DamageEnemy()
    {
        userController.Attack(userData.GetAttackPower());
    }
}
```
#### 단일 책임 원칙에 대한 생각
- 확실히 단일 책임 원칙을 잘 지킨다면 해당 스크립트, 클래스에서 손쉽게 유지보수 및 변경이 가능할 것 같다.
- 그리고 UserController에서 공격의 책임, 움직임의 책임 등등 좀 더 세밀하게도 나눌 수 있을 것같다.
- 하지만 이렇게 되었을 때 오히려 클래스의 수나 구조가 복잡해 질 수 있을 것 같다는 생각이 들었다.
- 책임이라는 것은 주관적인 범위이기에 적절히 구조를 생각해야할 것 같다.

### 2. 개방 폐쇄 원칙(OCP,Open-Closed Principle)
- 확장에 대해 열려있고 수정에 대해서는 닫혀있어야 한다는 것
- 확장에 대해 열려 있다는 것은 요구사항이 변경될 때 새로운 동작을 추가하여 기능을 확장 시킬 수 있게 하는 것
- 수정에 대해 닫혀 있다는 것은 기존의 코드를 수정하지 않고 동작을 추가하거나 변경할 수 있도록 하는 것
- 기존의 코드에 영향을 최소하는 것을 목표로 한다.
- 개방 폐쇄 원칙을 지키기 위해서는 추상화에 의존해야 한다.
- (출처 : https://mangkyu.tistory.com/194)


#### 내가 만들어본 예시 코드 
``` C#
public interface IItem
{
    void Use();
}
public class Item : IItem
{
    public void Use()
    {
        // 사용
    }
}

public class TestPlayer  : MonoBehaviour
{
    private IItem item = null;

    public void Start()
    {
        item = new Item();
    }

    public void UseItem()
    {
        if (item == null)
            return;

        item.Use();
    }
}
```
- 메서드를 오버로드 하도록 하기 위해 여러 인터페이스를 상속하는 경우
``` C#
public interface IItem
{
    void Use();
}

public interface IAutoAbleItem
{
    void Use(bool isAuto);
}

public class Item : IItem, IAutoAbleItem
{
    public void Use()
    {
        // 사용
    }

    public void Use(bool isAuto)
    {
        if(isAuto)
        {   
            // 자동 사용
        }
        else
        {
            // 수동 사용
        }

    }
}

public class TestPlayer  : MonoBehaviour
{
    private IItem item = null;
    private IAutoAbleItem autoItem = null;
    public void Start()
    {
        Item newItem = new Item();

        item = newItem;
        autoItem = newItem;
    }

    public void UseItem()
    {
        if (item == null)
            return;

        item.Use();
    }
    public void UseItem(bool isAtuo)
    {
        if (autoItem == null)
            return;

        autoItem.Use(isAtuo);
    }
}
```
#### 개방 폐쇄 원칙에 대한 생각
- 인터페이스에 대한 필요성은 예전부터 계속 생각해왔다.
- 하지만 개념에 대해 명확하지 않았고 혼자서 개발하는 경우 큰 필요성을 느끼지 못했다.
- 하지만 코드의 안전성 외에도 코드를 확장할 때 기존의 코드를 건드리지 않아도 되니 안전하게 할 수 있기 때문에 필수적인 것이다.
- 그리고 흔히 말하는 클래스간의 결합도를 낮추는 것은 중요하기에 좋은 역할을 할 수 있다.
- 앞서 한 예시는 해당 OCP를 적용하기에 어울리지는 않는 것 같다.
- 좀 더 적절한 사용처를 찾아봐야 할 것 같다.