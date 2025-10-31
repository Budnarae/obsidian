---
tags:
  - language/lua
  - just-in-time
  - translation
---

_들어가는 말_

---

## 1. 변수들

sol로 변수들을 다루는 것은 매우 쉽고, 이전에 다뤄봤을 법한 어떤 연관 배열(associative array)이나 맵(map) 구조와 거의 동일하게 동작합니다.

---

### 읽기 (reading)

다음과 같은 lua 파일이 sol로 불러와진다고 합시다:

```lua
config = {
	fullscreen = false,
	resolution = { x = 1024, y = 768 }
}
```

Lua 가상 머신(Lua Virtual Machine)과는 다음과 같이 상호작용할 수 있습니다:

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <tuple>
#include <assert.hpp>
#include <utility> // for std::pair

int main() {

	sol::state lua;
	lua.script_file("variables.lua");
	// "sol::state" 타입은 
	// 정확히 테이블처럼 동작합니다!
	bool isfullscreen = lua["config"]["fullscreen"]; // 중첩된 변수도 얻을 수 있음
	sol::table config = lua["config"];
	c_assert(!isfullscreen);
	return 0;
}
```

이 예시에서 보듯, 원하는 변수를 꺼내는 방법은 여러 가지입니다.  
예를 들어, 중첩된 변수가 존재하는지 확인하기 위해 `auto`를 사용해 `table[key]` 조회의 값을 캡처하고 `.valid()` 메서드를 사용할 수 있습니다:

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <tuple>
#include <assert.hpp>
#include <utility> // for std::pair

int main() {

	sol::state lua;
	lua.script_file("variables.lua");

	// test variable
	auto bark = lua["config"]["bark"];
	if (bark.valid()) {
		// 이 분기는 실행되지 않음: config 및/또는 bark는 변수가 아님
	}
	else {
		// 이 분기가 실행됨: config와 bark는 존재하는 변수임
	}

	return 0;
}
```

이 방법은 중첩된 변수가 존재하는지 확인할 때 유용합니다.  
또한 최상위 변수가 존재하는지 확인하려면 `sol::optional`을 사용할 수 있는데, 이는  
A) 접근하려는 키가 존재하는지, 그리고  
B) 가져오려는 타입이 특정 타입인지  
둘 다 확인해줍니다.

---

### optional lookup

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <tuple>
#include <assert.hpp>
#include <utility> // for std::pair

int main() {

	sol::state lua;
	lua.script_file("variables.lua");

	// optional도 사용 가능
	sol::optional<int> not_an_integer = lua["config"]["fullscreen"];
	if (not_an_integer) {
		// 이 분기는 실행되지 않음: 값이 정수가 아님
	}

	sol::optional<bool> is_a_boolean = lua["config"]["fullscreen"];
	if (is_a_boolean) {
		// 이 분기가 실행됨: 값이 boolean임
	}

	sol::optional<double> does_not_exist = lua["not_a_variable"];
	if (does_not_exist) {
		// 이 분기는 실행되지 않음: 해당 변수는 존재하지 않음
	}
	return 0;
}
```

이는 최적화 혹은 릴리스 모드에서도 안전성을 유지하며 검사를 수행할 때 유용합니다.  
또한 특정 값이 존재할 수도 있지만 기본값으로 대체하고 싶을 때 `get_or` 메서드를 사용할 수 있습니다:

---

### optional lookup (기본값)

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <tuple>
#include <assert.hpp>
#include <utility> // for std::pair

int main() {

	sol::state lua;
	lua.script_file("variables.lua");
	// 이 결과는 '24'가 됩니다.
	// (숫자를 가져오려 하지만 fullscreen은 숫자가 아님)
	int is_defaulted = lua["config"]["fullscreen"].get_or(24);
	c_assert(is_defaulted == 24);

	// 이 결과는 config의 실제 값인 'false'가 됩니다.
	bool is_not_defaulted = lua["config"]["fullscreen"];
	c_assert(!is_not_defaulted);

	return 0;
}
```

이렇게 하면 변수를 읽는 작업이 끝입니다!

---

### 쓰기 (writing)

쓰기 작업은 훨씬 간단합니다.  
파일이나 문자열을 스크립트로 실행하지 않아도, 마음대로 lua에 변수를 읽고 쓸 수 있습니다:

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <iostream>

int main() {

	sol::state lua;

	// 기본 lua 라이브러리들을 열기 
	// (print()와 같은 기본 유틸리티용)
	lua.open_libraries(sol::lib::base);

	// 전역 테이블의 값
	lua["bark"] = 50;

	// 전역 테이블 안에 테이블 생성
	lua["some_table"] = lua.create_table_with(
		"key0", 24,
		"key1", 25,
		lua["bark"], "the key is 50 and this string is its value!");

	// 평범한 lua 코드 문자열 실행
	// C++에서 sol을 통해 설정한 것들을 lua에서도 접근할 수 있음
	// "Raw String Literal" 사용으로 여러 줄 문자열 가능:
	// http://en.cppreference.com/w/cpp/language/string_literal
	lua.script(R"(
		
	print(some_table[50])
	print(some_table["key0"])
	print(some_table["key1"])

	-- lua 주석: lua 스크립트에서 전역 변수를 _G 테이블로 접근
	print(_G["bark"])

	)");

	return 0;
}
```

이 예시는 가능한 대부분의 작업을 보여줍니다.  
`lua["non_existing_key_1"] = 1` 구문은 그 변수를 생성하지만,  
테이블을 먼저 만들지 않고 너무 깊이 들어가면 Lua API가 패닉을 일으킵니다  
(예: `lua["does_not_exist"]["b"] = 20` 은 패닉 발생).

읽기/쓰기에서도 게으르게(lazy) 접근할 수 있습니다:

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <iostream>

int main() {

	sol::state lua;

	auto barkkey = lua["bark"];
	if (barkkey.valid()) {
		// 실행되지 않음: 아직 존재하지 않음
		std::cout << "How did you get in here, arf?!" << std::endl;
	}

	barkkey = 50;
	if (barkkey.valid()) {
		// 실행됨: 값이 존재함!
		std::cout << "Bark Bjork Wan Wan Wan" << std::endl;
	}

	return 0;
}
```

마지막으로, C++에서 `sol::lua_nil` 상수를 사용해 참조/변수를 nil로 설정하여 삭제할 수도 있습니다:

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <iostream>

int main() {

	sol::state lua;
	lua["bark"] = 50;
	sol::optional<int> x = lua["bark"];
	// x는 값을 가짐
	if (x) {
		std::cout << "x has no value, as expected" << std::endl;
	}
	else {
		return -1;
	}

	lua["bark"] = sol::lua_nil;
	sol::optional<int> y = lua["bark"];
	// y는 값을 가지지 않음
	if (y) {
		return -1;
	}
	else {
		std::cout << "y has no value, as expected" << std::endl;
	}

	return 0;
}
```

보시다시피 원하는 작업을 수행할 수 있는 방법은 다양합니다.  
하지만, 지금까지는 단순한 숫자와 문자열만 다뤘습니다.  
더 강력한 기능 — 즉, C++ 클래스나 함수 등을 넣고 싶다면 어떨까요?  
이제 그걸 섞어봅시다!

