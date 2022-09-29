# 웹(Web)이란...?

- World Wide Web의 줄임말로 전 세계적인 연결망을 나타낸다
- 브라우저를 통해 돌아나디는 가상의 연결망 세계 -> 브라우저를 통해 많은 웹 페이지를 돌아다니는 그림을 상상해보면됨
- 웹 페이지에 적혀있는 글은 Hyper Text라고 한다. 다른 텍스트에 대한 참조를 가지고 있는 텍스트이다.

# URL이란...?

- Uniform Resource Locator의 약자
- 웹에 존재하는 특정 데이터를 나타내는 문자열
- 웹에서 찾고자하는 데이터를 리소스(resource)라고 한다. 이 리소스를 찾을 수 있는 주소.  
   ex) https://www.codeitshopping.com/men/shirts?color=blue&size=m

  1.스킴(Scheme) : 프로토콜의 이름이 들어가는 부분 -> <u>https</U>  
  2.호스트(Host) : 전 세계 서버 중 하나의 서버를 특정 -> <u>www.codeitshopping.com</u>  
  3.경로(Path) : 서버에 있는 데이터 중 원하는 데이터를 특정(서버마다 다르게 설정된다) -> <u>/men/shirts</u>  
  4.쿼리(Query) : 데이터에 관한 세부적인 요구사항(url에 존재할 수도 있고 없을 수도 있다) -> <u>?color=blue&size=m</u>

# 프로토콜(protocol)이란...?

- 통신을 하는 두 주체가 지켜야 하는 통신 규약(웹 브라우저가 서버와 통신할 때 지켜야 하는 약속)
- https(Hyper Text Protocol Secure) -> 보안이 강화된 프로토콜
- https 규칙에 맞춰 요청을 보내면 서버도 이 규약에 맞춰 응답한다.

## 요청(request)를 보내면 일어나는 일

- 웹 브라우저로 특정 페이지에 접속할 때 보통 한 번 이상의 요청-응답이 오고간다  
  -> 첫 요청 안에서 또다시 요구되는, 여러가지 다른 것들을 구하기 위해 다시 여러개의 리퀘스트를 보낸다.

1. url에서 호스트 부분을 보고 어느 서버와 통신을 해야하는지 찾는다
2. 서버를 찾으면 웹 브라우저는 해당 서버로 요청을 보내는데 이때 path(path와 query)이후의 부분들을 담아서 부낸다
3. 서버는 이 요청에 담긴 path이후의 부분들을 보고, 그것이 의미하는 데이터를 찾고, 찾은 결과를 response에 담아서 보낸다.
4. 받은 response 내용을 갖고 사용자에게 보여준다.(response 내용은 다양하다).

# fetch API

- 서버로 요청을 보내고 응답을 받을 수 있다

1. fetch는 promise 객체르 리턴한다
2. then메소드를 사용해서 response가 왔을 때 실행될 콜백을 등록한다
3. 등록된 콜백들은 then 메소드로 등록한 순서대로 실행되고, 이때 이전 콜백의 리턴값을 다음 콜백이 넘겨받는다

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json()) // 실제 내용이 바로 넘어오는 것이 아니라 response에 관한 부가 정보와 함께 객체로 전달된다
  .then((result) => console.log(result)); // 그래서 실제 내용을 보려면 json으로 변환시켜야한다. 그리고 이 json 메소드의 리턴값이 실제 내용이된다
```

# JSON(JavaScript Object Notaion)

- 데이터 타입, 데이터 포멧
- 자바스크립트 문법과 거의 동일하다  
  ->객체와 배열을 나타내는 문법이 그대로 JSON에 쓰인다
- 반드시 큰 따옴표(")로 감싸준다
- JSON에서 사용할 수 없는 값들  
  -> undefined, NaN, infinity는 JSON에서 사용할 수 없다. 주석도 추가할 수 없다

### 요청(request)의 종류

CRUD(Create-Read-Update-Delete)  
리퀘스트의 메소드

1. 데이터 추가(POST-CREATE)
2. 데이터 조회(GET-READ)
3. 데이터 수정(PUT-UPDATE)
4. 데이터 삭제(DELETE-DELETE)

하나의 요청(request)는 Head와 Body로 이루어져있다.

Head: 요청에 대한 부가 정보가 들어있다. 메소드값과 url의 path도 들어있다.  
Body: 실제 데이터를 담는 부분이다. 데이터를 수정(PUT)하거나 추가(POST)하는 요청인 경우 필요하다. 나머지 경우(GET, DELETE)는 필요없음.

- 개발자 도구->Network->Headers->Request Headers(리퀘스트의 헤더부분이다)  
  Headers는 head안에 존재하는 하나 하나의 키와 값의 쌍을 의미한다.

```javascript
const url = "https://learn.codeit.kr/api/members";
// GET 요청 보내기
fetch(url)
  .then((res) => res.json())
  .then((result) => console.log(result));
```

```javascript
// POST 요청 보내기
const newMember = {
  name: "Sage",
  email: "sage@google.com",
  department: "engineering",
};
fetch(url, {
  method: "POST", // -> head에 설정되는 method 설정하기
  body: JSON.stringify(newMember), // -> stringify(): 객체를 문자열로 변환(직렬화)
})
  .then((res) => res.text())
  .then((result) => console.log(result));
```

```javascript
// PUT 요청 보내기
const changeInfo = {
  name: "Jason",
  email: "newEmail@naver.com",
  department: "sales",
};
fetch("https://learn.codeit.kr/api/members/1", {
  // -> PUT, DELETE 요청을 보내기 위해선 특정 url이 필요하다
  method: "PUT",
  body: JSON.stringify(changeInfo),
})
  .then((res) => res.text())
  .then((result) => console.log(result));
```

```javascript
// DELETE 요청 보내기
fetch("https://learn.codeit.kr/api/members/6", {
  method: "DELETE",
})
  .then((res) => res.text())
  .then((result) => console.log(result));
```
