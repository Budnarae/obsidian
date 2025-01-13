
---

#language/JavaScript 

*temporal dead zone*

---

자바스크립트 언어는 코드를 해석하기 전 변수의 초기화에 관련된 코드를 변수의 **선언**과 **초기화**로 분리한 뒤, 변수의 선언 부분만 컨텍스트의 최상단 부분으로 끌어올린다. 그리고 일시적으로 **undefined**를 할당한다. 이러한 동작을 ==호이스팅 hoisting==이라고 한다.

이러한 특성 때문에 **var** 키워드로 선언된 변수는 변수의 초기화 이전에 사용해도 별다른 에러가 출력되지 않는다. 단지 undefined가 할당될 뿐이다.

```javascript

console.log(i);
var i = "I an a variable";

// undefined

console.log(j);
let j = "I an a let";

// ReferenceError: can't access lexical declaration `j' before initialization

```

하지만 **let

---

참고자료

#참고도서/모던_자바스크립트_핵심_가이드 

---