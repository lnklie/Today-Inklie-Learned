문자열(string) 클래스에 대하여
=======
- C++ STL에서 제공하는 클래스, 문자열을 다루는 클래스
- C에서는 char* 또는 char[]의 형태로 문자열을 다뤘지만, C++에서는 문자열을 하나의 변수 type으로 사용
- char*, char[]과 다르게 문자열 끝에 '\0'문자가 들어가지 않음, 문자열의 길이를 동적으로 변경 가능
- string 은 문자를 += 하면 덧붙이게 된다!! 
- 예제
``` c++
#include <iostream>
#include <string.h>
using namespace std;

string code(int re, char s[20]) {
	string result;
	for (int i = 0; i < strlen(s); i++) {
		for (int j = 0; j < re; j++) {
			result += s[i];
		}
	}
	return result;
}

int main() {
	char s[20];
	int n,repeat;
	cin >> n;
	for (int i = 0; i < n; i++) {
		cin >> repeat >> s;
		cout << code(repeat, s) << endl;
	}
	return 0;
}
```
string 클래스의 입/출력
-------
- C++입출력 방식은 cin, cout으로 입출력이 가능, getline함수도 이용할 수 있다.
- scanf와 printf는 사용이 불가능

``` c++
// 문자열 생성
string str;

// 공백 이전까지의 문자열일 입력
cin >> str;

// '\n'이전까지의 문자열을 입력 받음, 한줄 통째로
getline(cin, str); 

// 'a'문자 이전까지의 문자열을 입력받음
getline(cin, str, 'a') 

// 문자열 출력
cout << str;
```

string 클래스 생성
------
- string 헤더 파일 추가

``` c++
// 빈 문자열 생성
string str;

// "Inklie"로 선언된 str 생성
string str = "Inklie";

// 또는
string str;
str = "Inklie";

// 생성자를 이용한 생성
string str("Inklie");

// 복사 생성자
string str2("str1");

// C 문자열과 호환도 가능
char s[] = {'I', 'n', 'k', 'l', 'i', 'e'};
string str(s);

// new를 이용한 동적할당
string *str = new string("Inklie");
```

- <,>, == 같은 연산자도 사용할 수 있음
- <, >, == 는 사전 순서를 비교
- +는 문자열을 이어는 역할
- size()함수는 문자열 길이 출력

멤버함수
------
- 참고 자료 참고

활용 예제
-----
``` c++
#include <iostream>
using namespace std;

int main(void)
{
	string _name;

	cin >> _name;
	if (_name.size() > 50)
		return 0;
	cout << _name + "??!";
}
```
- 문자열 + 배열 활용
``` c++
#include <iostream>

using namespace std;
int main(void)
{
    ios::sync_with_stdio(false);
    cin.tie(NULL);

    int num = 0;
    int num2 = 0;
    int point = 0;
    cin >> num;
    int* totalNum = new int[num] {0,};
    while (num2 < num)
    {
        string temp;
        cin >> temp;
        if (temp.size() < 0 || temp.size() > 80)
            return 0;
        for (int i = 0; i < temp.size(); i++)
        {
            if (temp[i] != 'O' && temp[i] != 'X')
                return 0;
            else
            {
                if (temp[i] == 'O')
                {
                    point++;
                }
                else
                {
                    point = 0;
                }
            }
            totalNum[num2] += point;
        }
        num2++;
        point = 0;
    }
    for (int i = 0; i < num2; i++)
    {
        cout << totalNum[i]<< endl;
    }
}
```

### 문자열 + 2차원 배열 관련 예제

``` c++
#include <iostream>
#include <string.h>
using namespace std;

bool isAlphaNumeric(char* str)
{
	char* alpa = new char[] {"0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ\\$%*+-./:"};
	bool _bool = false;
	for (int i = 0; i < strlen(str); i++)
	{
		for (int j = 0; j < strlen(alpa); j++)
		{
			if (str[i] == alpa[j])
				_bool = true;
		}
	}
	return _bool;
}
int main()
{
	int testNum = 0;
	cin >> testNum;
	char** save = new char* [testNum];
	for (int i = 0; i < testNum; i++)
		save[i] = new char[61]{};
	int index = 0;
	while (index < testNum)
	{
		int num = 0;
		cin >> num;
		char a[21];
		cin >> a;
		if (!isAlphaNumeric(a))
			return 0;
		char* temp = new char[strlen(a) * num + 1];

		int c = 0;
		for (int i = 0; i < strlen(a) + 1; i++)
		{
			for (int j = 0; j < num; j++)
			{
				temp[c + j] = a[i];
			}
			c += num;
		}

		save[index] = temp;
		
		index++;
	}
	for (int i = 0; i < testNum; i++)
	{
		cout << save[i] << endl;
	}
}
```

참고 자료
------
https://rebro.kr/53