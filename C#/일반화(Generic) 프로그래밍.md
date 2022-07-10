일반화 프로그래밍(Generic Programming)에 대하여
==========
- 작성한 하나의 코드가 여러 가지 데이터 형식에 맞춰 동작할 수 있도록 하는 것
- 공통된 개념을 찾아 묶는 것이 일반화
- 일반화하는 대상은 <데이터 형식>
<br><br>
일반화 메소드
--------
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
<br><br>
- 출력할 때는 
```cs
int[] i_source = {1, 2, 3, 4, 5};
int[] i_target = new int[i_source.Length];

CopyArray<int>(i_source, i_target);

foreach(int element in target);
    Console.WriteLine(element);
```
<br><br>
일반화 클래스
---------
```cs
class 클래스 이름<형식 매개 변수>
{
    // ...
}
```
``` cs
class Array_Int
{
    private int[] array;
    public int GetElement(int index){return array[index];}
}

class Array_Float
{
    private float[] array;
    public float GetElement(int index) {return array[index];}
}

// 해당 형식들을 

class Array_Generic<T>
{
    private T[] array;
    public T GetElement(int index){return array[index];}
}
// 이렇게 일반화 시킬 수 있음
```
- 인스턴스 생성시 <형식>을 넣어주면 됨
``` cs
Array_Generic<int> intArr = new array_Generic<int>();
Array_Generic<double> dblArr = new array_Generic<double>();
```
- 예제
```cs
class MyList<T>
{
    private T[] array;

    public MyList()
    {
        array = new T[3];
    }

    public T this[int index]
    {
        get
        {
            return array[index];
        }
        set
        {
            if(index >= array.Length)
            {
                Array.Resize<T>(ref array, index + 1);
                Console.WriteLine($"Array Resized : {array.Length}");
            }
            array[index] = value;
        }
    }
    
    public int Length
    {
        get {return array.Length;}
    }
}
```
- 인스턴스를 생성할 때 내부 배열에 접근하여 해당 인덱스 값을 얻거나 넣고 사이즈가 3이상이라면 resize 해주는 예제




