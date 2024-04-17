
---

#language #cpp 

*constant*

---

**const**는 대상을 상수화시키는 역할을 한다.

아래와 같이 사용될 수 있다.

1. 변수의 상수화

```cpp

const int num = 10;
//num = 20; -> error : 변경 불가

```

2. 포인터의 상수화
	
+ 포인터 자체를 상수화

```cpp

int * const ptr = &val;
//ptr = &val2; -> error

```

+ 참조를 통해 값을 변경할 수 없음

```cpp

int const *ptr = &val;
//*ptr = 4; -> error

```

3. [[클래스]]의 멤버함수를 const로 선언. const 함수는 아래의 특징을 가진다.
	+ 함수 내부에서 멤버 변수의 값 변경 불가.
	+ 

---

참고자료

[윤성우의 열혈 c++ 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589147)

---