
---

#language/JavaScript #web 

_REpresentational State Transfer_

---

# REST API

**REST**는 HTTP를 기반으로 클라이언트가 서버의 리소스에 접근하는 방식을 규정한 아키텍처고, REST API는 REST를 기반으로 서비스 API를 구현한 것을 의미한다.

REST의 기본 원칙을 성실히 지킨 서비스 디자인을 **RESTful**하다고 표현한다.

# REST API의 구성

REST API는 **자원 resource, 행위 verb, 표현 representation**의 3가지 요소로 구성된다. REST는 **자체 표현 구조 self-descripitiveness**로 구성되어 REST API만으로 HTTP 요청의 내용을 이해할 수 있다.

| 구성 요소            | 내용                           | 표현 방법        |
| -------------------- | ------------------------------ | ---------------- |
| 자원 resource        | 자원                           | URI(엔드 포인트) |
| 행위 verb            | 자원에 대한 행위               | HTTP 요청 메서드 |
| 표현 representations | 자원에 대한 행위의 구체적 내용 | 페이로드         |

# REST API 설계 원칙

REST에서 가장 중요한 기본적인 원칙은 두 가지다. **URI는 리소스를 표현**하는 데 집중하고, 행위에 대한 정의는 HTTP 요청 메서드를 통해 하는 것이 **RESTful API**를 설계하는 중심 규칙이다.

## URI는 리소스를 표현해야 한다.

URI는 리소스를 표현하는 데 중점을 두어야 한다. 리소스를 식별할 수 있는 이름은 동사보다는 명사를 사용한다. 따라서 이름에 get 같은 행위에 대한 표현이 들어가서는 안 된다.

```

# bad
GET /getTodos/1
GET /todos/show/1

# good
GET /todos/1

```

## 리소스에 대한 행위는 HTTP 요청 메서드로 표현한다.

HTTP 요청 메서드는 클라이언트가 서버에게 요청의 종류와 목적(리소스에 대한 행위)를 알리는 방법이다. 주로 5가지 요청 메서드(GET, POST, PUT, PATCH, DELETE 등)을 사용하여 CRUD를 구현한다.

| HTTP 요청 메서드 | 종류           | 목적                  | 페이로드 |
| ---------------- | -------------- | --------------------- | -------- |
| GET              | index/retrieve | 모든/특정 리소스 취득 | X        |
| POST             | create         | 리소스 생성           | O        |
| PUT              | replace        | 리소스의 전체 교체    | O        |
| PATCH            | modify         | 리소스의 일부 수정    | O        |
| DELETE           | delete         | 모든/특정 리소스 삭제 | X         |

리소스에 대한 행위는 HTTP 요청 메서드를 통해 표현하며 URI에 표현하지 않는다. 예를 들어, 리소스를 취득하는 경우에는 GET, 리소스를 삭제하는 경우에는 DELETE를 사용하여 리소스에 대한 행위를 명확히 표현한다.

```

# bad
GET /todos/delete/1

# good
DELETE /todos/1

```

## JSON Server를 이용한 REST API 실습

HTTP 요청을 전송하고 응답을 받으려면 서버가 필요하다. JSON Server를 사용해 가상 REST API 서버를 구축하여 HTTP 요청을 전송하고 응답을 받는 실습을 진행해보자.

### JSON Server 설치

JSON Server는 json 파일을 사용하여 가상 REST API 서버를 구축할 수 있는 툴이다.
다음과 같이 [[npm]]을 사용하여 설치한다.

```bash

mkdir json-server && cd json-server
npm init -y
npm install json-server --save-dev

```

### db.json 파일 생성

프로젝트 루트 폴더(/json-server)에 다음과 같이 db.json 파일을 생성한다. db.json 파일은 리소스를 제공하는 데이터베이스 역할을 한다.

```json

{
    "todos": [
        {
            "id": 1,
            "content": "HTML",
            "completed": true
        },
        {
            "id": 2,
            "content": "CSS",
            "completed": false
        },
        {
            "id": 3,
            "content": "JavaScript",
            "completed": true
        }
    ]
}

```

### JSON Server 실행

package.json 파일의 scripts를 다음과 같이 수정하여 JSON Server를 실행하여 보자. package.json 파일에서 불필요한 항목은 삭제하였다.

```json

{
  "name": "json-server",
  "version": "1.0.0",
  "scripts": {
    "start": "json-server --watch db.json"
  },
  "devDependencies": {
    "json-server": "^1.0.0-beta.3"
  }
}

```

터미널에서 `npm start` 명령어를 입력하여 JSON Server를 실행한다.

### GET 요청

#### 모든 todo 취득하기

todos 리소스에서 모든 todo를 취득(index)한다.

JSON Server의 루트 폴더(/json-server)에 public 폴더를 생성하고 JSON Server를 중단한 후 재실행한다. 그리고 public 폴더에 다음 get_index.html을 추가하고 브라우저에서 `http://localhost:3000/get_index.html`로 접속한다.

```html

<!DOCTYPE html>
<html>
    <body>
        <pre></pre>
        <script>
            // XMLHttpRequest 객체 생성
            const xhr = new XMLHttpRequest();

            // HTTP 요청 초기화
            // todos 리소스에서 모든 todo를 취득(index)
            xhr.open('GET', '/todos');

            // HTTP 요청 전송
            xhr.send();

            // load 이벤트는 요청이 성공적으로 완료된 경우 발생한다.
            xhr.onload = () => {
                // status 프로퍼티 값이 200이면 정상적으로 응답된 상태다.
                if (xhr.status === 200)
                {
                    document.querySelector('pre').textContent = xhr.response;
                }
                else
                {
                    console.error('Error', xhr.status, xhr.statusText)
                }
            };
        </script>
    </body>
</html>

```

#### 특정 todo 취득(retrieve)하기

todos 리소스에서 id를 사용하여 특정 todo를 취득(retrieve)한다. public 폴더에 다음 get_retrieve.html을 추가하고 브라우저에서 `http://localhost:3000/get_retrieve.html`로 접속한다.

```html

<!DOCTYPE html>
<html>
    <body>
        <pre></pre>
        <script>
            // XMLHttpRequest 객체 생성
            const xhr = new XMLHttpRequest();

            // HTTP 요청 초기화
            // todos 리소스에서 id를 사용하여 특정 todo를 취득(retrieve)
            xhr.open('GET', '/todos/1');

            // HTTP 요청 전송
            xhr.send();

            // load 이벤트는 요청이 성공적으로 완료된 경우 발생한다.
            xhr.onload = () => {
                if (xhr.status === 200)
                {
                    document.querySelector('pre').textContent = xhr.response;
                }
                else
                {
                    console.error('Error', xhr.status, xhr.statusText);
                }
            };
        </script>
    </body>
</html>

```

### POST 요청

todos 리소스에 새로운 todo를 생성한다. POST 요청 시에는 setRequestHeader 메서드를 사용하여 요청 몸체에 담아 서버로 전송할 페이로드의 MIME 타입을 지정해야 한다.

public 폴더에 다음 post.html을 추가하고 브라우저에서 `http://localhost:3000/post.html`로 접속한다.

```html

<!DOCTYPE html>
<html>
    <body>
        <pre></pre>
        <script>
            // XMLHTTPRequest 객체 생성
            const xhr = new XMLHttpRequest();

            // HTTP 요청 초기화
            // todos 리소스에 새로운 todo를 생성
            xhr.open('POST', '/todos');

            // 요청 몸체에 담아 서버로 전송할 페이로드의 MIME 타입을 지정
            xhr.setRequestHeader('content-type', 'application/json');

            // HTTP 요청 전송
            // 새로운 todo를 생성하기 위해 페이로드를 서버에 전송해야 한다.
            xhr.send(JSON.stringify({ id: 4, content: 'Angular', completed: false }));

            // load 이벤트는 요청이 성공적으로 완료된 경우 발생한다.
            xhr.onload = () => {
                // status 프로퍼티 값이 200(OK) 또는 201(Created)이면 정상적으로 응답된 상태다.
                if (xhr.status === 200 || xhr.status === 201) {
                    document.querySelector('pre').textContent = xhr.response;
                }
                else {
                    console.error('Error', xhr.status, xhr.statusText);
                }
            };
        </script>
    </body>
</html>

```

### PATCH 요청

PATCH는 특정 리소스의 일부를 수정할 때 사용한다. 다음 예제에서는 todos 리소스의 id로 todo를 특정하여 completed만 수정한다. PATCH 요청 시에는 setRequestHeader 메서드를 사용하여 요청 몸체에 담아 서버로 전송할 페이로드의 MIME 타입을 지정해야 한다.

public 폴더에 다음 patch.html을 추가하고 브라우저에서 `http://localhost:3000/patch.html`로 접속한다.

```html

<!DOCTYPE html>
<html>
    <body>
        <pre></pre>
        <script>
            // XMLHttpRequest 객체 생성
            const xhr = new XMLHttpRequest();
            
            // HTTP 요청 초기화
            // todos 리소스의 id로 todo를 특정하여 completed만 수정
            xhr.open('PATCH', '/todos/4');

            // 요청 몸체에 담아 서버로 전송할 페이로드의 MIME 타입을 지정
            xhr.setRequestHeader('content-type', 'application/json');

            // HTTP 요청 전송
            // 리소스를 수정하기 위해 페이로드를 서버에 전송해야 한다.
            xhr.send(JSON.stringify({ completed: false }));

            // load 이벤트는 요청이 성공적으로 완료된 경우 발생한다.
            xhr.onload = () => {
                // status 프로퍼티 값이 200이면 정상적으로 응답된 상태다.
                if (xhr.status === 200) {
                    document.querySelector('pre').textContent = xhr.response;
                }
                else
                {
                    console.error('Error', xhr.status, xhr.statusText);
                }
            };
        </script>
    </body>
</html>

```

### DELETE 요청

todos 리소스에서 id를 사용하여 todo를 삭제한다. public 폴더에 다음 delete.html을 추가하고 브라우저에서 `http://localhost:3000/delete.html`로 접근한다.

```javascript

<!DOCTYPE html>
<html>
    <body>
        <pre></pre>
        <script>
            // XMLHttpRequest 객체 생성
            const xhr = new XMLHttpRequest();

            // HTTP 요청 초기화
            // todos 리소스에서 id를 사용하여 todo를 삭제한다.
            xhr.open('DELETE', '/todos/4');

            // HTTP 요청 전송
            xhr.send();

            // load 이벤트는 요청이 성공적으로 완료된 경우 발생한다.
            xhr.onload = () => {
                // status 프로퍼티 값이 200이면 정상적으로 응답된 상태다.
                if (xhr.status === 200) {
                    document.querySelector('pre').textContent = xhr.response;
                }
                else {
                    console.error('Error', xhr.status, xhr.statusText);
                }
            };
        </script>
    </body>
</html>

```

---

참고자료

#참고도서/모던_자바스크립트_Deep_Dive 

---