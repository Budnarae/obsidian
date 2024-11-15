
---

#language/cpp 

---

객체 기반의 배열은 다음의 형태로 선언한다.

```cpp

Obj arr[10];

```

이를 동적으로 할당하는 경우에는 다음의 형태로 선언한다.

```cpp

Obj * ptrArr = new Obj[10];

```

이러한 형태로 배열을 선언하면, 열 개의 객체가 모여 배열을 구성하는 형태가 된다. 이렇듯 구조체 배열의 선언과 차이가 없다. 하지만 배열을 선언하는 경우에도 생성자는 호출이 된다. 단, 배열의 선언과정에서는 호출할 생성자를 별도로 명시하지 못한다(생성자에 인자를 전달하지 못한다.) 즉, 위의 형태로 배열이 형성되려면 다음 형태의 생성자가 반드시 정의되어 있어야 한다.

```cpp

Obj() { . . . . }

```

---

참고자료

#참고도서/윤성우의_열혈_cpp_프로그래밍

---