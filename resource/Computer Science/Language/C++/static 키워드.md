
---

#language #cpp 

*static*

---

기존의 C 언어에서 static 키워드는 다음의 의미를 가진다.

- 전역 변수에 선언된 static의 의미 -> 선언된 파일 내에서만 참조를 허용하겠다는 의미
- 함수 내에 선언된 static의 의미 -> 한번만 초기화되고, 지역변수와 달리 함수를 빠져나가도 소멸되지 않는다.

C++에서 static 키워드는 추가적으로 다음의 의미를 가진다.

1. static 키워드가 멤버 변수에 붙은 경우
	- static 멤버변수는 **클래스 매개변수**라고도 한다. 일반적인 멤버변수와 달리 클래스당 하나씩만 생성되기 때문이다.
	- static 변수는 클래스의 객체가 생성되지 않아도 전역 변수와 같이 메모리 공간에 할당된다.
	- 만일 객체가 여러 개 생성된다면 여러 개의 객체가 하나의 static 변수를 공유한다.
	- static 함수의 소멸 시점은 전역 변수와 동일하다.
	- static 멤버변수는 적어도 한번은 초기화되어야 하며, 초기화는 생성자 내부가 아닌 곳에서 별도로 이루어져야 한다.
	- static 멤버변수는 객체를 통하지 않아도 다음과 같이 접근이 가능하다.
		- `cout<<SoSimple::simObjcnt;`cpp

*static 멤버변수를 선언하는 예제코드*

```cpp

class SoSimple
{
	private :
		static int simObjCnt; //static 멤버변수, 클래스 변수
	public :
		SoSimple()
		{
			simObjCnt++;
			cout<<simObjCnt<<"번째 SoSimple 객체"<<endl;
		}
};
int SoSimple::simObjCnt = 0; //static 멤버 변수의 초기화. static 멤버 변수는 반드시 단 한번은 초기화가 이루어져야 한다.

```

![[static 멤버변수.png]]

---

참고자료

[윤성우의 열혈 c++ 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589147)

---