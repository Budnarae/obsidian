
---

#language/csharf #platform #translation

_.NET tutorial_

---

# C# 콘솔 앱 템플릿의 최상위 문 생성

.NET 6부터 콘솔 앱 템플릿의 변화

.NET 6부터 새로운 C# 콘솔 앱 프로젝트 템플릿은 Program.cs 파일에 다음 코드를 생성한다:
C#

// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello, World!");

이 새로운 출력은 프로그램에 필요한 코드를 간소화하는 최신 C# 기능을 사용한다. .NET 5 및 이전 버전의 경우, 콘솔 앱 템플릿은 다음 코드를 생성한다:
C#

using System;

namespace MyApp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}

위 코드에서 실제 네임스페이스는 프로젝트 이름에 따라 달라진다.

이 두 가지 형식은 동일한 프로그램을 나타낸다. 둘 다 C#에서 유효하다. 새로운 버전을 사용하면 Main 메서드의 본문만 작성하면 된다. 컴파일러가 진입점 메서드를 가진 Program 클래스를 생성하고 모든 최상위 문을 해당 메서드에 배치한다. 생성된 메서드의 이름은 Main이 아니며, 코드가 직접 참조할 수 없는 구현 세부 사항이다. 다른 프로그램 요소를 포함할 필요가 없으며, 컴파일러가 자동으로 생성한다. C# 가이드의 기초 섹션에 있는 최상위 문에 대한 문서에서 최상위 문을 사용할 때 컴파일러가 생성하는 코드에 대해 더 자세히 알아볼 수 있다.

.NET 6 이상 템플릿을 사용하도록 업데이트되지 않은 튜토리얼을 다루는 두 가지 방법이 있다:

    새로운 프로그램 스타일을 사용하여 기능을 추가하면서 새로운 최상위 문을 추가한다.
    새로운 프로그램 스타일을 Program 클래스와 Main 메서드를 가진 이전 스타일로 변환한다.

이전 템플릿을 사용하려면 이 문서의 뒷부분에 있는 "이전 프로그램 스타일 사용"을 참조한다.
