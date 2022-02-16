# Fetch API

- HTTP요청 전송 기능을 제공하는 클라이언트 사이드 Web API다.
- fetch는 HTTP 응답을 나타내는 Response 객체를 래핑한 Promise 객체를 반환한다.  
  -> 후속 처리 메소드 then을 통해 Response 객체를 전달받을 수 있다.
- 기본 문법  
  : 첫 번째 인수로는 요청을 전송할 URL을 전달하고  
  두 번째 인수로는 HTTP요청 메소드, 요청 헤더, 페이로드 등을 설정한 객체를 전달한다.

```javascript
const promise = fetch(url[,options]);
```

---
- 실습을 위해 임시로 만든 json데이터  
  : 파일명: users.json
```json
{
  "userList": [
    {
      "name": "user1",
      "level": "A"
    },
    {
      "name": "user2",
      "level": "B"
    },
    {
      "name": "user3",
      "level": "C"
    },
    {
      "name": "user4",
      "level": "A"
    },
    {
      "name": "user5",
      "level": "B"
    },
    {
      "name": "user6",
      "level": "C"
    }
  ]
}
```

```javascript
fetch("users.json") //
  .then((res) => console.log(res.json())); // json 데이터 타입으로 변환
// Promise {<pending>} -> promise를 반환하기 때문에 후속 처리 메소드 then을 사용할 수 있다.
```

```javascript
fetch("users.json")
  .then((res) => res.json())
  .then((data) => console.log(data));
// {userList: Array(6)} -> 변환된 데이터를 출력하면 users.json 파일에 있는 배열 형태의 데이터를 얻을 수 있다.
```
