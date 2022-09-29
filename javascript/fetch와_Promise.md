# fetch 함수와 Promise

- 비동기 실행은 동일한 작업을 더 빠른 시간 내에 처리할 수 있다.
- fetch 함수는 promise 객체를 리턴한다. -> promise 후속 처리 메소드가 사용가능하다.

### Promise 객체란...?

- 어떤 작업에 관한 상태 정보를 가지고 있는 객체  
  -> fetch 함수가 서버와 통신한 결과를 promise 객체에 저장해 리턴한다.

  <b>Promise 객체는 3가지 상태를 가진다.</b>

1. Pending : 진행중
2. fulfilled : 성공
3. rejected : 실패

제일 처음 fetch 함수가 리턴한 promise 객체는 pending 상태이다.  
 그 후에 response를 잘 받으면 fulfilled 상태가 된다. 실패시 pending에서 rejected 상태가 된다.

<b>상태와 결과는 다르다...?</b>

pending에서 fulfilled나 rejected 상태가 되면 그 결과도 추가적으로 갖는다.  
 fulfilled 상태가 되었을 때 그 결과를 then 메소드에 등록해놓은 콜백함수의 첫 번째 파라미터로 넘겨준다.

### Promise 객체가 등장한 이유

1. callback hell 문제를 해결한다
2. 비동기 처리 작업에 관한 좀 더 세밀한 처리를 할 수 있다.

```javascript
console.log("Start!");
fetch("https://jsonplaceholder.typicode.com/users") // 작업 상태를 담은 프로미스 객체를 리턴
  .then((response) => response.text()) // 작업 결과를 콜백의 파라미터(response)로 전달
  .then((result) => {
    console.log(result);
  });
console.log("End");
```

### Promise Chaining

- 비동기 처리를 순차적으로 처리해야할 때 전체 코드를 좀 더 깔끔하게 나타내기 위해서 사용한다.
- then 메소드는 <u>새로운 프로미스 객체</u>를 리턴한다. 그래서 then 메소드 다음에 또다른 then 메소드를 연결해서 사용할 수 있다.
- then 메소드가 리턴하는 promise 객체는 처음에는 pending 상태이다.  
  그러나 then 메소드에 등록되어 있는 콜백이 리턴하는 값에 따라 그 상태에 영향을 준다.

1. 콜백이 promise 객체를 리턴하는 경우 : 콜백이 리턴하는 promise 객체와 then 메소드가 리턴하는 promise 객체가 동일한 상태와 결과를 갖는다.
2. 콜백이 promise 객체가 아닌 값을 리턴하는 경우 : then 메소드가 리턴하는 promise 객체는 fulfilled 상태가 되고 콜백의 리턴값이 결과값이 된다.

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((result) => {
    const userId = result[0].id;
    return fetch(`https://jsonplaceholder.typicode.com/posts?userId=${userId}`);
  }) // fetch 함수가 리턴하는 Promise 객체가 해당 then 메소드가 리턴하는 promise 객체와 동일한 상태를 가진다.
  .then((response) => response.json())
  .then((result) => {
    console.log(result);
  });
```

<b>p.s)</b>  
3. 콜백이 아무 값도 리턴하지 않는 경우 : 함수가 아무것도 리턴하지 않으면 undefined를 리턴하는 것으로 간주된다.  
4. 실행된 콜백 내부에서 에러가 발생했을 때 -> 이 경우에는 Promise 객체가 rejected 상태가 되고, 작업 실패 정보로 해당 에러 객체를 갖게 된다.  
5. 아무런 콜백도 실행되지 않을 때
만약 rejected 상태가 되었는데 두 번째 콜백이 등록되어 있지 않는 경우라면?  
 -> 해당 then 메소드는 이전 Promise 객체랑 동일한 상태와 결과를 갖는다. 즉, 똑같이 rejected 상태와 결과를 갖는다.

## rejected 상태가 되면?

1. 첫 번째 콜백은 fulfilled 상태일 때 실행될 콜백을 등록하고 두 번째 콜백은 rejected 상태일 때 실행될 콜백을 등록한다.

- 두 번째 콜백의 파라미터로는 작업 실패 정보가 넘어간다.

```javascript
fetch("http://jsonplaceholder.typicode.com/users")
  .then(
    (response) => response.json(),
    // 두 번째 콜백: rejected 상태가 되었을 때 실행될 콜백
    (error) => {
      console.log(error);
    }
  )
  .then((result) => {
    console.log(result);
  });
```

2. catch 메소드 사용

- promise 객체가 rejected 상태가 되면 실행될 콜백을 등록한다
- then 메소드를 약간 변형 시킨 메소드이다. -> `then(undefined, (error) => {console.log(error)})`이 코드와 동일함
- 어느 promise 객체가 rejected 상태가 되더라도 잘 대응하기 위해서는 catch 메소드를 마지막에 써주는 것이 좋다.

```javascript
fetch("http://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  // rejected 상태가 되면 실핼될 catch 메소드 등록
  .catch((error) => {
    console.log(error);
  })
  .then((result) => {
    console.log(result);
  });
```

```javascript
fetch("http://jsonplaceholder.typicode.com/user") // 잘못된 URL
  .then((res) => res.json())
  .then((result) => {
    console.log(result);
    throw new Error("test");
  })
  // 제일 마지막에 catch 메소드 사용
  .catch((error) => {
    console.log(error);
  });
```

### finally 메소드

- fulfilled 상태나 rejected 상태에 상관없이 항상 처리해야하는 작업이 있을 때 사용
- 작업 성공 결과나 실패 정보가 없기 때문에 파라미터가 필요없다.
- 보통 catch 메소드 바로 뒤에 위치한다.

```javascript
fetch("http://jsonplaceholder.typicode.com/users")
  .then((res) => res.json())
  .then((result) => {
    console.log(result);
    throw new Error("test");
  })
  .catch((error) => {
    console.log(error);
  })
  // catch 이후에 finally 메소드 사용
  .finally(() => {
    console.log("exit");
  });
```
