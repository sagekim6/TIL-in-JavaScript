# Promisify와 상태가 결정된 Promise 객체

## Promisify

- 기존의 전통적인 형식의 비동기 실행 함수도 원한다면 <u>프로미스화</u>해서 사용할 수 있다.
- 기존의 비동기 실행 함수들 중에서도 그 콜백을 한번만 실행하는 것들(setTimeout, readFile 등)만 Promisify해서 사용가능하다.  
  -> settled상태에선 pending상태로 다시 변할 수 없음

```javascript
// 전통적인 비동기 형식 -> setTimeout 함수
function wait(text, milliseconds) {
  setTimeout(() => text, milliseconds); // setTimeout 함수의 리턴 값만 있다
}
// wait 함수의 리턴값은 따로 없다.

fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.text())
  .then((result) => wait(`${result}`, 2000)) // -> wait 함수의 리턴값이 없기 때문에 undefind가 나온다.
  .then((result) => {
    console.log(result);
  });
```

<b>wait 함수가 promise 객체를 리턴하게 promisify과정을 거친다.</b>

```javascript
function wait(text, milliseconds) {
  // promise 객체 생성 후 변수에 할당
  const p = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(text);
    }, milliseconds);
  });
  return p; // promise 객체를 리턴
}

fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.text())
  .then((result) => wait(`${result}`, 2000))
  .then((result) => {
    console.log(result);
  });
```

## 이미 상태가 결정된 Promise 객체 만들기

- new 생성자와 executor 함수를 사용하지않고 resolve 메소드나, reject 메소드를 사용한다.
- 함수 안에서 리턴하는 값이 여러 개인 경우 모든 리턴값을 Promise 객체로 통일하고 싶을 때, 종종 resolve 또는 reject 메소드를 사용.

1. fulfilled 상태인 promise 객체

- resolve 메소드를 사용해 fulfilled상태인 promise 객체 만들기

```javascript
// fulfilled 상태인 promise 객체 생성, 작업 성공 결과로는 'success'문자열을 갖는다.
const fulfilledP = Promise.resolve("success");
```

2. rejected 상태인 promise 객체

- reject 메소드를 사용해 rejected상태인 promise 객체 만들기

```javascript
// rejected 상태인 promise 객체 생성, 작업 실패 결과로는 'fail'메시지를 가진 에러 객체를 생성.
const rejectedP = Promise.reject(new Error("fail"));
```
