---
tags:
  - language/lua
  - just-in-time
  - translation
---

_들어가는 말_

---

# 변수들

sol로 변수들을 다루는 것은 매우 쉽고, 이전에 다뤄봤을 법한 어떤 연관 배열(associative array)이나 맵(map) 구조와 거의 동일하게 동작합니다.

---

## 읽기 (reading)

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

## optional lookup

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

## optional lookup (기본값)

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

## 쓰기 (writing)

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

---

# functions and You

sol은 모든 종류의 함수를 등록할 수 있습니다. 빠른 예제(quick ‘n’ dirty)에서도 여러 예시가 나왔지만, 여기서는 sol로 감싸진 Lua 시스템에 함수를 등록할 수 있는 다양한 추가 방법들을 다룹니다.

---

## 새로운 함수 설정하기 (Setting a new function)

C++ 함수가 주어지면, 변수를 설정하는 것과 매우 비슷한 방식으로 여러 가지 방법으로 sol에 넣을 수 있습니다.

### Registering C++ functions

```cpp
#include <sol/sol.hpp>

std::string my_function( int a, std::string b ) {
        // 문자 'D'를 "a"번 반복한 문자열을 만들고,
        // 그것을 'b'에 이어붙임
        return b + std::string( 'D', a );
}

int main () {

        sol::state lua;

        lua["my_func"] = my_function; // 방법 1
        lua.set("my_func", my_function); // 방법 2
        lua.set_function("my_func", my_function); // 방법 3

        // 이 함수는 이제 'my_func'라는 이름으로
        // 이 상태(state)에서 실행되는 lua 스크립트 / 코드에서 접근 가능
        lua.script("some_str = my_func(1, 'Da')");

        // 방금 실행된 Lua 코드의 전역 변수 'some_str'을 읽어옴
        std::string some_str = lua["some_str"];
        // some_str == "DaD"
}
```

같은 코드가 클래스의 멤버 함수/멤버 변수 포인터, 람다(lambda) 함수에도 똑같이 동작합니다.

---

## Registering C++ member functions

```cpp
struct my_class {
        int a = 0;

        my_class(int x) : a(x) {

        }

        int func() {
                ++a; // a를 1 증가시킴
                return a;
        }
};

int main () {

        sol::state lua;

        // 여기서는 멤버 함수와 클래스 인스턴스를 바인딩함:
        // 지정된 클래스 인스턴스에서 함수를 호출하게 됨
        lua.set_function("my_class_func", &my_class::func, my_class());

        // 여기서는 클래스 인스턴스를 전달하지 않음:
        // Lua에서 이 함수를 호출하려면 "my_class"의 인스턴스를 직접 넘겨야 함
        lua.set_function("my_class_func_2", &my_class::func);

        // 사전 바인딩된 인스턴스 사용:
        lua.script(R"(
                first_value = my_class_func()
                second_value = my_class_func()
        )");
        // first_value == 1
        // second_value == 2

        // 인스턴스 미바인딩 버전 사용:
        lua.set("obj", my_class(24));
        // Lua에서 "obj"로 참조되는 클래스 인스턴스에 대해 "func" 호출
        lua.script(R"(
                third_value = my_class_func_2(obj)
                fourth_value = my_class_func_2(obj)
        )");
        // third_value == 25
        // fourth_value == 26
}
```

이런 식으로 설정하면 **클래스의 멤버 함수와 멤버 변수**는 모두 함수로 변환됩니다.  
C++을 Lua에서 다룰 수 있도록 하는 **usertype(사용자 정의 타입)** 섹션을 배우면 `obj.a = value` 형태의 직관적인 변수 접근이 가능해지지만, 지금은 함수만 다루고 있습니다.

---

## 함수 템플릿에 대한 설명

많은 사람이 궁금해하는 점 중 하나가 함수 템플릿입니다.  
템플릿 함수(멤버 함수이든 자유 함수이든)는 **C++에서 인스턴스화(instantiation)** 되기 전까지 존재하지 않기 때문에 그대로 등록할 수 없습니다.  
즉, 아래와 같은 템플릿 함수가 있다면:

### A C++ templated function

```cpp
template <typename A, typename B>
auto my_add( A a, B b ) {
        return a + b;
}
```

모든 템플릿 인자를 명시적으로 지정해 주어야 바인딩할 수 있습니다.

---

### Registering function template instantiations

```cpp
int main () {

        sol::state lua;

        // 두 정수를 더함
        lua["my_int_add"] = my_add<int, int>;

        // 두 문자열을 연결함
        lua["my_string_combine"] = my_add<std::string, std::string>;

        lua.script("my_num = my_int_add(1, 2)");
        int my_num = lua["my_num"];
        // my_num == 3

        lua.script("my_str = my_string_combine('bark bark', ' woof woof')");
        std::string my_str = lua["my_str"];
        // my_str == "bark bark woof woof"
}
```

여기서 두 개의 별도 함수를 바인딩했습니다.  
하지만 **하나의 함수 이름**으로 호출할 때 **인자 타입에 따라 다르게 동작**하게 만들고 싶다면 어떨까요?  
이것을 **오버로딩(Overloading)** 이라고 하며, `sol::overload`를 이용해 다음과 같이 구현할 수 있습니다.

---

### Registering C++ function template instantiations

```cpp
int main () {

        sol::state lua;

        // 두 정수를 더하거나 두 문자열을 결합
        lua["my_combine"] = sol::overload( my_add<int, int>, my_add<std::string, std::string> );

        lua.script("my_num = my_combine(1, 2)");
        lua.script("my_str = my_combine('bark bark', ' woof woof')");
        int my_num = lua["my_num"];
        std::string my_str = lua["my_str"];
        // my_num == 3
        // my_str == "bark bark woof woof"
}
```

이 기능은 여러 타입을 받을 수 있고, 타입에 따라 다르게 동작해야 하는 함수에 유용합니다.  
원한다면 여러 오버로드를 추가할 수 있으며, 타입이 다양해도 괜찮습니다.

---

💡 **참고:**  
기본 인자를 가진 함수(default parameters)는 자동으로 여러 버전으로 바인딩되지 않습니다.  
기본 인자를 지원하려면 직접 `sol::overload`를 사용해야 합니다.

또한, 람다나 호출 가능한 구조체(callable struct)를 바인딩할 때 어떤 식으로 동작하는지 잘 이해해야 합니다.

---

## Lua로부터 함수 가져오기 (Getting a function from Lua)

Lua에서 함수를 가져오는 방법은 두 가지가 있습니다.  
하나는 `sol::function`, 또 하나는 더 고급 버전인 `sol::protected_function` 입니다.

이 둘을 사용하면 Lua에서 정의된 callable을 가져와 C++에서 호출할 수 있습니다.

---

### Retrieving a sol::function

```cpp
int main () {

        sol::state lua;

        lua.script(R"(
                function f (a)
                        return a + 5
                end
        )");

        // 즉시 가져와서 바로 호출
        int x = lua ;
        // x == 35

        // 먼저 저장해두고 나중에 호출
        sol::function f = lua["f"];
        int y = f(20);
        // y == 25
}
```

`set_function` 등으로 C++에서 바인딩한 함수 역시 같은 방식으로 가져올 수 있습니다.

`sol::protected_function`은 `sol::function`과 비슷하지만, **에러 처리 핸들러(error_handler)** 를 설정할 수 있다는 점이 다릅니다.  
이 핸들러는 모든 오류를 잡아 처리할 수 있습니다.

---

### Retrieving a sol::protected_function

```cpp
int main () {
        sol::state lua;

        lua.script(R"(
                function handler (message)
                        return "Handled this message: " .. message
                end

                function f (a)
                        if a < 0 then
                                error("negative number detected")
                        end
                        return a + 5
                end
        )");

        sol::protected_function f = lua["f"];
        f.error_handler = lua["handler"];

        sol::protected_function_result result = f(-500);
        if (result.valid()) {
                // 호출 성공
                int x = result;
        }
        else {
                // 호출 실패
                sol::error err = result;
                std::string what = err.what();
                // 'what'의 내용:
                // "Handled this message: negative number detected"
        }
}
```

---

## Lua와의 다중 반환 (Multiple returns to and from Lua)

Lua와 C++ 사이에서 여러 값을 주고받을 때는  
C++의 `std::tuple` 또는 `std::pair` 클래스를 사용하면 됩니다.  
또는 `sol::tie`를 이용해 미리 선언한 변수들에 직접 할당할 수도 있습니다.

---

### Multiple returns from Lua

```cpp
int main () {
        sol::state lua;

        lua.script("function f (a, b, c) return a, b, c end");

        std::tuple<int, int, int> result;
        result = lua["f"](1, 2, 3);
        // result == { 1, 2, 3 }

        int a, b;
        std::string c;
        sol::tie( a, b, c ) = lua["f"](1, 2, "bark");
        // a == 1
        // b == 2
        // c == "bark"
}
```

---

### Multiple returns into Lua

C++에서 Lua로 여러 값을 반환할 수도 있습니다.  
예를 들어, C++의 람다를 Lua에 바인딩한 후, Lua에서 호출하면 `std::tuple`로 여러 값을 반환할 수 있습니다.

```cpp
int main () {
        sol::state lua;

        lua["f"] = [](int a, int b, sol::object c) {
                // sol::object는 어떤 타입이든 가능: 그대로 전달
                return std::make_tuple( a, b, c );
        };

        std::tuple<int, int, int> result = lua["f"](1, 2, 3);
        // result == { 1, 2, 3 }

        std::tuple<int, int, std::string> result2;
        result2 = lua["f"](1, 2, "Arf?")
        // result2 == { 1, 2, "Arf?" }

        int a, b;
        std::string c;
        sol::tie( a, b, c ) = lua["f"](1, 2, "meow");
        // a == 1
        // b == 2
        // c == "meow"
}
```

여기서 `sol::object`는 Lua에서 들어오는 “아무 값(any value)”을 전달하기 위한 수단입니다.  
또한 `sol::make_object`를 이용해 C++ 값으로부터 Lua 객체를 만들어 반환할 수도 있습니다.

---

## Any return to and from Lua

(아무 타입이나 Lua로 주고받기)

앞의 예제에서도 언급했듯이, `sol::object`는 **“아무 타입(any type)”** 을 Lua로 전달할 때 유용합니다.  
이는 C++ 표준에 `std::variant<...>` 가 완전히 도입될 때까지의 대안 역할을 합니다.

`sol::object`는 `sol::this_state`와 함께 다음처럼 사용할 수 있습니다.

---

### Return anything into Lua

```cpp
sol::object fancy_func (sol::object a, sol::object b, sol::this_state s) {
        sol::state_view lua(s);
        if (a.is<int>() && b.is<int>()) {
                return sol::make_object(lua, a.as<int>() + b.as<int>());
        }
        else if (a.is<bool>()) {
                bool do_triple = a.as<bool>();
                return sol::make_object(lua, b.as<double>() * ( do_triple ? 3 : 1 ) );
        }
        return sol::make_object(lua, sol::lua_nil);
}

int main () {
        sol::state lua;

        lua["f"] = fancy_func;

        int result = lua["f"](1, 2);
        // result == 3
        double result2 = lua["f"](false, 2.5);
        // result2 == 2.5

        // Lua에서 호출, 결과 받기
        lua.script("result3 = f(true, 5.5)");
        double result3 = lua["result3"];
        // result3 == 16.5
}
```

---

이로써 **함수(Functions)** 와 sol 간의 상호작용에 대해 거의 모든 것을 다뤘습니다.  
좀 더 고급 트릭이나 기능을 배우고 싶다면 `sol::this_state`와 `sol::variadic_args`를 참고하세요.  
다음 튜토리얼 주제는 **C++ 타입(usertypes)을 Lua에서 사용하는 방법**입니다.  
C++ 쪽 함수의 인자 활용법이나 효율적인 사용법이 더 궁금하다면 관련 노트를 참고하세요.