어셈블리(Assembly)에 대하여
=======
- 어셈블리는 .NET기반 애플리케이션에 대한 배포, 버전 제어, 재사용, 활성화 범위 및 보안 권한의 기본 단위를 형성
- 어셈블리는 서로 함께 사용되어 논리적 기능 단위를 형성하도록 빌드되는 형식 및 리소스의 컬렉션
- 실행 파일(.exe) 또는 동적 연결 라이브러리(.dll)파일의 형태를 가지며 .NET 애플리케이션의 구성 요소
- 형식 구현을 인식하는 데 필요한 정보와 함께 공용 언어 런타임을 제공
<br/><br/>
- .NET 및 .NET Framework에서, 소스 코드 파일 1개 이상에서 어셈블리를 빌드할 수 있음
- .NEY Framework에서, 어셈블리 모듈을 하나 이상 포함할 수 있음
- 대규모 프로젝트를 계획하여 여러 개발자가 작업하는 별도의 소스 코드 파일이나 모듈을 결합하여 단일 어셈블리를 만들 수 있음

속성
-----
1. .exe 또는 dll파일로 구현
2. .NET Framework를 대상으로 하는 라이브러리의 경우 GAC(전역 어셈블리 캐시)에 어셈블리를 넣으면 애플리케이션간에 어셈블리를 공유할 수 있음
3. GAC에 어셈블리를 포함하려면 먼저 강력한 이름의 어셈블리를 만들어야함
4. 어셈블리는 필요한 경우에만 메모리에 로드, 사용되지 않는 경우에는 로드되지 않음. 대규모 프로젝트에서 리소스를 관리하는 효율적인 방법일 수 있음
5. 리플렉션을 사용하여 프로그래밍 방식으로 어셈블리에 대한 정보를 얻을 수 있음
6. .NET 및 .NET Framework에서 MetadataLoadContext 클래스를 사용하여 어셈블리를 검사하기 위해 로드할 수 있음, MetadataLoadContext는 Assembly.ReflectionOnlyLoad 메소드를 바꿈

리플렉션
-----

참고자료
------
https://docs.microsoft.com/ko-kr/dotnet/standard/assembly/ - 어셈블리    
https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/concepts/reflection - 리플렉션