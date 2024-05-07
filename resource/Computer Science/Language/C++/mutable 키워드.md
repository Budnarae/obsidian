
---

#language #cpp 

*mutable*

---

**mutable**은 다음의 의미를 가진 키워드이다.

*const 함수 내에서의 값의 변경을 예외적으로 허용한다.*

아래의 예제와 같이 사용할 수 있다.

```cpp

#include <iostream>
using namespace std;

class SoSimple
{
	private:
		int num1;
		mutable int num2;
	public :
}


```

---

참고자료

[윤성우의 열혈 c++ 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589147)

---