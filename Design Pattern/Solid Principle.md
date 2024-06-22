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
