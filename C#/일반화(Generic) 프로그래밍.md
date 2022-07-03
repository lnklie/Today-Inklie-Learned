일반화 프로그래밍(Generic Programming)에 대하여
==========
- 작성한 하나의 코드가 여러 가지 데이터 형식에 맞춰 동작할 수 있도록 하는 것
- 공통된 개념을 찾아 묶는 것이 일반화
- 일반화하는 대상은 <데이터 형식>
<br><br>
```cs
void CopyArray(int[] source, int[] target)
{
    for(int i = 0; i < source.Length; i++>)
        target[i] = source[i];
}

void CopyArray(string[] source, string[] target)
{
    for(int i = 0; i < source.Length; i++)
        target[i] = source[i];
}
```
- 이렇게 오버로딩을 사용에 매개변수를 여러 형식을 사용하게 할 수 있지만
```cs
void CopyArray<T>(T[] source, T[] target)
{
    for(int i = 0 ; i < source.Length; i++)
        target[i] = source[i];
}
```
- 이렇게 만들어주면 형식매개변수를 사용하여 매소드를 사용할 때 다양한 형식을 사용할 수 있게 된다.


