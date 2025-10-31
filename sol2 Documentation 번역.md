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
        int x = lua["f"](30);
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

---

## C++ in Lua

사용자 정의 타입(“usertype” 또는 간단히 “udt”)을 sol에서 사용하는 것은 간단합니다.  
만약 멤버 변수나 함수를 호출하지 않는다면, 굳이 ‘등록(register)’할 필요도 없습니다 — 그냥 그대로 전달하면 됩니다.  
하지만 Lua 안에서 usertype의 변수와 함수를 사용하려면, 반드시 등록을 해야 합니다.

여기서는 여러 가지 정보를 포함한 짧은 예시를 통해 usertype을 다루는 방법을 보여드리겠습니다.

---

### player.hpp

```cpp
#include <iostream>

struct player {
public:
	int bullets;
	int speed;

	player()
		: player(3, 100) {

	}

	player(int ammo)
		: player(ammo, 100) {

	}

	player(int ammo, int hitpoints)
		: bullets(ammo), hp(hitpoints) {

	}

	void boost() {
		speed += 10;
	}

	bool shoot() {
		if (bullets < 1)
			return false;
		--bullets;
		return true;
	}

	void set_hp(int value) {
		hp = value;
	}

	int get_hp() const {
		return hp;
	}

private:
	int hp;
};
```

이 클래스는 비교적 단순하지만, Lua에서 메타테이블(metatable)을 직접 작성하는 일은 피하고 싶습니다.  
우리는 이 클래스를 Lua에 **손쉽게 통합**하고 싶습니다.

---

### 우리가 Lua에서 사용하고 싶은 코드 (player_script.lua)

```lua
p1 = player.new(2)

-- p2는 아래에서 lua["p2"] = player(0); 으로 설정되어 있으므로 여전히 존재함
local p2shoots = p2:shoot()
assert(not p2shoots)
-- 탄약이 0이었음

-- 변수 프로퍼티 설정자(setter)
p1.hp = 545
-- 프로퍼티 접근자(unqualified getter)로 값 얻기
print(p1.hp)
assert(p1.hp == 545)

local did_shoot_1 = p1:shoot()
print(did_shoot_1)
print(p1.bullets)
local did_shoot_2 = p1:shoot()
print(did_shoot_2)
print(p1.bullets)
local did_shoot_3 = p1:shoot()
print(did_shoot_3)

-- 읽기 가능
print(p1.bullets)
-- 아래는 오류 발생: bullets는 읽기 전용 변수이므로 쓸 수 없음
-- p1.bullets = 20

p1:boost()
-- Lua 스크립트에서 런타임에 정의한 함수 호출
p1:brake()
```

---

이 동작을 가능하게 하려면, `new_usertype`과 `method`를 사용해 바인딩해야 합니다.  
이 메서드들은 `table`과 `state(_view)` 양쪽 모두에 존재하지만, 여기서는 `state`를 사용하겠습니다.

---

### main.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include "player.hpp"

#include <iostream>

int main() {
	sol::state lua;

	lua.open_libraries(sol::lib::base);

	// usertype을 등록하기 전에 userdata를 설정해도 괜찮음.
	// 이후에 usertype을 등록하면 올바른 메타테이블이 자동으로 연결됨.

	// "p2"라는 변수를 player 타입(탄약 0)으로 설정
	lua["p2"] = player(0);

	// usertype 메타테이블 생성
	sol::usertype<player> player_type = lua.new_usertype<player>("player",
		// 3개의 생성자
		sol::constructors<player(), player(int), player(int, int)>());

	// 값을 반환하는 일반적인 멤버 함수
	player_type["shoot"] = &player::shoot;
	// 일반적인 멤버 함수
	player_type["boost"] = &player::boost;

	// 멤버 변수처럼 get/set 가능한 프로퍼티
	player_type["hp"] = sol::property(&player::get_hp, &player::set_hp);

	// 읽기/쓰기 가능한 변수
	player_type["speed"] = &player::speed;
	// 읽기 전용 변수
	// .set(foo, bar)는 [foo] = bar 와 동일
	player_type.set("bullets", sol::readonly(&player::bullets));

	lua.script_file("prelude_script.lua");
	lua.script_file("player_script.lua");
	return 0;
}
```

---

### 추가 Lua 코드 (prelude_script.lua)

```lua
function player:brake ()
	self.speed = 0
	print("we hit the brakes!")
end
```

이 스크립트는 C++에서 정의되지 않은 `brake` 메서드를 **Lua 쪽에서 동적으로 추가**하는 예시입니다.

---

이제 이 스크립트를 실행하면 잘 작동할 것입니다.  
값의 변화를 관찰하거나 실험도 가능하죠.

이 밖에도 다음과 같은 고급 기능들이 존재합니다:

- 초기화 함수 (private 생성자 / 소멸자 지원)
    
- `name.my_function(...)` 형태로 호출 가능한 “정적(static)” 함수
    
- 오버로딩된 멤버 함수
    
- `sol::var`을 이용한 전역 변수 바인딩 (`std::ref`를 사용하면 참조로도 가능)
    

---

이 방법은 단순히 함수를 등록하는 수준을 넘어,  
**Lua에서 C++ 코드를 재활용할 수 있는 강력한 방법**입니다.

더 복잡한 클래스나 자료 구조를 Lua에 노출할 수 있으며,  
만약 usertype 이상의 세밀한 제어가 필요하다면  
`sol`의 커스터마이징 및 확장 기능을 통해 원하는 동작을 정의할 수도 있습니다.

더 많은 예시와 복잡한 코드는 `examples` 디렉터리의  
`usertype_` 접두어가 붙은 예시들을 참고하면 됩니다.

---

## **소유권 (ownership)**

C++에서 리소스를 관리할 때 소유권은 중요합니다.  
**sol**은 여러 가지 소유권(ownership) 의미 체계를 가지고 있으며, 대부분 기본적으로 안전합니다.  
아래는 그 규칙들입니다.

---

### **객체 소유권 (object ownership)**

Lua에 존재하는 어떤 것에 대한 참조를 가져오려면 `sol::reference` 또는 `sol::object`를 통해 가져올 수 있습니다:

#### object_lifetime.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <string>
#include <iostream>

int main () {
	sol::state lua;
	lua.open_libraries(sol::lib::base);

	lua.script(R"(
	obj = "please don't let me die";
	)");

	sol::object keep_alive = lua["obj"];
	lua.script(R"(
	obj = nil;
	function say(msg)
		print(msg)
	end
	)");

	lua.collect_garbage();

	lua["say"](lua["obj"]);
	// 여전히 여기서 접근 가능하며 Lua 내에서도 살아 있음
	// 이름이 지워졌더라도
	std::string message = keep_alive.as<std::string>();
	std::cout << message << std::endl;

	// Lua에 다시 인자로 전달하거나
	// 새 이름으로 지정할 수도 있음
	// 원하는 대로!
	lua["say"](keep_alive);

	return 0;
}
```

모든 객체는 `sol::state`가 파괴되기 전에 반드시 파괴되어야 합니다.  
그렇지 않으면 Lua 상태(Lua State)에 대한 **dangling reference(잘못된 참조)** 가 생겨  
끔찍하고 무시무시한 방식으로 프로그램이 터질 것입니다. 💥

이 규칙은 단지 `sol::object`에만 해당되지 않습니다.  
`sol::reference` 및 `sol::object`에서 파생된 모든 타입 (`sol::table`, `sol::userdata`, 등등) 역시  
**state가 범위를 벗어나기 전에 정리(clean up)** 되어야 합니다.

---

### **포인터 소유권 (pointer ownership)**

`sol`은 **raw pointer (일반 포인터)** 의 소유권을 가져가지 않습니다.  
Raw pointer는 어떤 것도 소유하지 않기 때문입니다.

따라서 `sol`은 raw pointer를 삭제하지 않습니다.  
(삭제하면 안 됩니다. 소유자가 아니기 때문입니다.)

#### pointer_lifetime.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

struct my_type {
	void stuff() {
	}
};

int main() {

	sol::state lua;
	// AAAHHH BAD
	// dangling pointer!
	lua["my_func"] = []() -> my_type* { return new my_type(); };

	// AAAHHH!
	lua.set("something", new my_type());

	// AAAAAAHHH!!!
	lua["something_else"] = new my_type();
	return 0;
}
```

---

대신 **unique_ptr** 또는 **shared_ptr** 을 사용하거나,  
단순히 **값(value)** 자체를 반환하세요.

#### (스마트 포인터 사용) pointer_lifetime.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

struct my_type {
	void stuff() {
	}
};

int main() {

	sol::state lua;
	// :ok:
	lua["my_func0"] = []() -> std::unique_ptr<my_type> { return std::make_unique<my_type>(); };

	// :ok:
	lua["my_func1"] = []() -> std::shared_ptr<my_type> { return std::make_shared<my_type>(); };

	// :ok:
	lua["my_func2"] = []() -> my_type { return my_type(); };

	// :ok:
	lua.set("something", std::unique_ptr<my_type>(new my_type()));

	std::shared_ptr<my_type> my_shared = std::make_shared<my_type>();
	// :ok:
	lua.set("something_else", my_shared);

	// :ok:
	auto my_unique = std::make_unique<my_type>();
	lua["other_thing"] = std::move(my_unique);

	return 0;
}
```

---

만약 **수명이 충분히 길어질 것임을 확실히 알고 있고**,  
Lua에 **참조(reference)** 로 넘기기만 하려는 것이라면  
그것도 괜찮습니다:

#### (static) pointer_lifetime.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

struct my_type {
	void stuff() {
	}
};

int main() {

	sol::state lua;
	lua["my_func5"] = []() -> my_type* {
		static my_type mt;
		return &mt;
	};
	return 0;
}
```

---

`sol`은 **nullptr** 을 감지할 수 있습니다.  
따라서 반환할 때 nullptr이면,  
dangling 참조 대신 **sol::lua_nil** 값이 푸시됩니다.

하지만 **미리 nil임을 알고 있다면**,  
`std::nullptr_t` 또는 `sol::lua_nil` 을 명시적으로 반환하는 것이 좋습니다.

#### (nil / nullptr) pointer_lifetime.cpp

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

struct my_type {
	void stuff() {
	}
};

int main() {

	sol::state lua;
	// 이건 여전히 나쁨 DON'T DO IT AAAHHH BAD
	// 빈 unique_ptr을 반환하거나
	// 명시적으로 하세요!
	lua["my_func6"] = []() -> my_type* { return nullptr; };

	// :ok:
	lua["my_func7"] = []() -> std::nullptr_t { return nullptr; };

	// :ok:
	lua["my_func8"] = []() -> std::unique_ptr<my_type> {
		// 기본 생성되며 nullptr로 초기화됨
		// Lua로는 nil로 푸시됨
		return std::unique_ptr<my_type>();
		// std::shared_ptr도 동일하게 동작함
	};

	// 허용됨, 'something'을 nil로 설정함
	// (참조가 없으면 다음 GC 때 삭제됨)
	lua.set("something", nullptr);

	// 이것도 괜찮음
	lua["something_else"] = nullptr;

	return 0;
}
```

---

### **일시적 (ephemeral, proxy) 객체**

**Proxy** 와 **result** 타입들은 **일시적(ephemeral)** 입니다.  
이들은 Lua 스택에 의존하며, 생성자와 소멸자가 Lua 스택과 상호작용합니다.

즉, 이런 객체들은 **C++ 함수에서 반환하기에 매우 위험**합니다.  
(매우 신중한 관리 없이는 스택이 해제된 후 참조 오류가 발생합니다.)

다음과 같은 스택 기반 객체들을 사용할 때 주의해야 합니다:

- `protected_function_result`
    
- `function_result`
    
- `load_result`
    
- `stack_reference`
    
- 그 밖의 Lua 스택을 직접 다루는 타입들
    

이런 것들을 반환하고 싶다면, **다시 생각해보세요**.  
특히 **여러 개의 load/function 결과를 한 C++ 함수에서 처리하는 경우**는  
구현 세부사항(implementation-defined behavior)에 의존해야 하므로  
매우 위험합니다.

---

✅ **정리 요약**

- `sol::object`, `sol::table` 등은 **Lua state보다 오래 살아서는 안 됨**
    
- **raw pointer 사용 금지**, 대신 `unique_ptr` / `shared_ptr` / 값 사용
    
- **nullptr 반환 시 nil로 처리됨**
    
- **스택 기반 객체는 반환하지 말 것**
    

---

## **자신만의 타입 추가하기 (Adding your own types)**

가끔은 `sol`이 특정 구조체(struct)나 클래스(class)를 단순히 `userdata`로 처리하는 것 대신,  
다른 방식으로 다루도록 **직접 오버라이드(override)** 하고 싶을 때가 있습니다.

이를 위해서는 `sol`이 제공하는 **4가지 커스터마이즈 지점(customization point)** 을 활용해야 합니다.  
이들은 다음과 같습니다:

- `sol_lua_check`
    
- `sol_lua_get`
    
- `sol_lua_push`
    
- `sol_lua_check_get`
    

이들은 **템플릿 클래스/구조체**이므로, C++에서 **특수화(specialization)** 를 통해 오버라이드합니다.

아래는 C++ → Lua 방향으로 갈 때 구조체를 **두 개의 값으로 분해**하고,  
Lua → C++으로 돌아올 때 다시 **하나의 구조체로 재조합**하는 예시입니다:

---

### **main.cpp**

```cpp
#define SOL_ALL_SAFETIES_ON 1
#include <sol/sol.hpp>

#include <iostream>
#include "assert.hpp"

struct two_things {
	int a;
	bool b;
};

template <typename Handler>
bool sol_lua_check(sol::types<two_things>, lua_State* L, int index, Handler&& handler, sol::stack::record& tracking) {
	// 인덱스는 음수일 수 있으며, 이는 스택의 위에서부터 카운트합니다.
	// 이를 처리하기 위해 lua_absindex 함수를 이용해 절대 인덱스로 변환합니다.
	int absolute_index = lua_absindex(L, index);
	// 첫 번째와 두 번째 인덱스가 올바른 타입인지 검사합니다.
	bool success = sol::stack::check<int>(L, absolute_index, handler) && sol::stack::check<bool>(L, absolute_index + 1, handler);
	tracking.use(2);
	return success;
}

two_things sol_lua_get(sol::types<two_things>, lua_State* L, int index, sol::stack::record& tracking) {
	int absolute_index = lua_absindex(L, index);
	// 첫 번째 요소를 가져옵니다.
	int a = sol::stack::get<int>(L, absolute_index);
	// 두 번째 요소는 첫 번째로부터 +1 위치에서 가져옵니다.
	bool b = sol::stack::get<bool>(L, absolute_index + 1);
	// 우리는 2개의 슬롯을 사용합니다 (int 1개, bool 1개)
	tracking.use(2);
	return two_things { a, b };
}

int sol_lua_push(lua_State* L, const two_things& things) {
	int amount = sol::stack::push(L, things.a);
	// amount는 1입니다: int는 스택에 1개의 항목을 푸시함
	amount += sol::stack::push(L, things.b);
	// amount는 2가 됩니다: bool도 1개의 항목을 푸시함
	// 두 가지 값을 반환
	return amount;
}

int main() {
	std::cout << "=== customization ===" << std::endl;
	std::cout << std::boolalpha;

	sol::state lua;
	lua.open_libraries(sol::lib::base);
```

---

이것이 여러분이 자신만의 클래스로 확장할 때 따라야 할 **기본 공식(base formula)** 입니다.  
이후 라이브러리의 다른 부분에서도 매끄럽게 사용할 수 있습니다.

---

### **main.cpp (계속)**

```cpp
	// 단순 pass-through 스타일의 함수를 생성합니다.
	lua.script("function f ( a, b ) print(a, b) return a, b end");

	// Lua에서 함수를 가져옵니다.
	sol::function f = lua["f"];

	two_things things = f(two_things { 24, false });
	c_assert(things.a == 24);
	c_assert(things.b == false);
	// things.a == 24
	// things.b == true

	std::cout << "things.a: " << things.a << std::endl;
	std::cout << "things.b: " << things.b << std::endl;
	std::cout << std::endl;

	return 0;
}
```

---

이것으로 끝입니다! 🎉

---

### **구현에 대한 몇 가지 주의사항**

1. `sol::stack::record` 타입의 보조 매개변수(auxiliary parameter)가  
    **getter와 checker 함수들에 사용**됩니다.  
    이는 마지막으로 완료된 작업을 추적하기 위한 것입니다.
    
    위 예시에서는 두 멤버를 가져왔으므로  
    `tracking.use(2);` 를 호출해 **2개의 스택 위치를 사용**했음을 표시했습니다.  
    (하나는 `int`, 하나는 `bool`)
    
2. 또한 `index` 매개변수를 사용하고,  
    그 다음 멤버를 위해 **index + 1** 을 사용한 점에 주목하세요.
    

---

만약 여러분이 어떤 타입을 Lua로 **푸시(push)** 할 수 있도록 만들고 싶지만  
Lua에서 **가져올(get)** 필요는 없다면,  
시스템의 한 부분만 **특수화(specialization)** 하면 됩니다.

- Lua에서 값을 **가져와야 하는 경우**  
    → `sol::stack::getter` 와 `sol::stack::checker` 템플릿 클래스를 특수화해야 합니다.
    
- Lua로 **값을 푸시해야 하는 경우**  
    → `sol::stack::pusher` 템플릿 클래스를 특수화해야 합니다.
    
- `sol::lua_size` 템플릿 클래스 특성(trait)도 두 경우에 대해 특수화해야 하지만,  
    만약 한 개의 아이템만 푸시(push)한다면  
    기본 구현(default implementation)이 자동으로 1을 가정합니다.
    

---

### ⚠️ **주의사항 (Note)**

여기서 중요한 점은,  
`get`, `push`, `check` 함수들은 `T` 타입과 `T*` (포인터 타입)를 **구별한다**는 것입니다.

즉, 만약 `T`와 동일하지 않은 의미 체계를 가진 `T*` 핸들을  
독립적으로 다루고 싶다면,  
`T*` 와 `T` **둘 다에 대한 checker/getter/pusher** 를 정의해야 할 수도 있습니다.

- `T*`의 **checker** 는 `T`의 checker를 **forward** 하지만,
    
- `T*`의 **getter** 는 `T`의 getter로 **forward되지 않습니다.**  
    (예: `int*`는 `int`와 다르기 때문입니다.)
    

---

일반적으로 대부분의 getter/checker는 **스택의 한 지점만 사용**하므로 문제가 없습니다.  
하지만 **복잡한 중첩 클래스(nested class)** 를 다룬다면,  
`tracking.last` 를 이용해  
마지막 `get` 또는 `check` 작업이 몇 개의 스택 인덱스를 사용했는지 확인한 후,  
`stack::check<..>(L, index, tracking)` 호출 뒤에  
`index + tracking.last` 로 증가시키는 것이 유용합니다.

---

더 자세한 내용은 **stack 관련 API 페이지**에서  
확장 포인트(extension point)에 대한 설명을 확인할 수 있습니다.

또한 무언가 잘못되었거나 추가적인 질문이 있다면  
**GitHub Issues 페이지**에 글을 남기거나 **이메일로 문의**해 주세요!

---

✅ **요약**

- `sol_lua_check`, `sol_lua_get`, `sol_lua_push` 등을 통해 **사용자 정의 타입 변환 가능**
    
- `sol::stack::record`는 스택 사용량 추적용
    
- `T`와 `T*`는 **별개로 처리됨**
    
- getter/checker/pusher를 적절히 **특수화(specialize)** 하면  
    C++ ↔ Lua 간 사용자 정의 타입을 자유롭게 주고받을 수 있음
    

---

원문 표현, 코드, 설명 모두 포함한 완전한 번역입니다.  
원하신다면 여기서 이어지는 “stack customization API” 문서 부분도 번역해드릴까요?