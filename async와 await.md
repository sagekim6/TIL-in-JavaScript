# async와 await

async/await 구문을 쓰는 이유는

1. 개발자가 더 편하게 작성할 수 있도록 하고
2. 코드의 가독성을 높이기 위해  
   Promise 객체를 사용할 때, then 메소드를 사용하지 않고도 마치 동기 실행 코드처럼 코드를 훨씬 더 간단하고 편하게 작성할 수 있다.

### async

- 함수의 function 키워드 앞에 위치한다. -> 해당 함수안에 비동기적으로 실행되는 코드가 있다고 알려주는 의미
- async가 붙은 해당 함수는 항상 프로미스를 반환한다. 프로미스가 아닌 값이라도 프로미스 상태로 감싼 후 리턴한다.

### await

- async가 붙은 함수 안에서만 동작한다.(일반 함수 안에서 사용하면 에러가 발생한다.)
- await 키워드를 만나면 프로미스가 처리될 때까지 기다렸다가 그 결과를 반환한다.

```javascript
fetch("http://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((result) => {
    console.log(result);
  });
```

```javascript
// 위의 fetch 함수 코드를 async와 await을 이용해 작성함
async function fetchAndPrint() {
  const response = await fetch("http://jsonplaceholder.typicode.com/users"); // fetch 함수가 fulfilled 상태가 될 때까지 기다렸다가 작업 성공 결과가 담긴 response 객체를 리턴한다.
  const result = await response.json(); // response의 실제 내용이 변수 result에 담긴다.
  console.log(result);
}
fetchAndPrint();
```

### 실행 순서

- async 함수 안의 코드가 실행되다가 await을 만나면 일단 await 뒤의 코드가 실행된다.  
  그리고 async 함수 바깥으로 나가서 나머지 코드를 실행한다.

```javascript
async function fetchAndPrint() {
  console.log(2); // 2
  const response = await fetch("http://jsonplaceholder.typicode.com/users"); // fetch 함수를 실행 시키고 다시 함수가 실행된 지점으로 돌아간다.
  console.log(7); // 7
  const result = await response.json(); // await을 만나면 await 뒤에 있는 코드를 먼저 실행시키고 다시 실행 흐름은 async 함수 바깥으로 나가게된다.
  console.log(result);
}

console.log(1); // 1
fetchAndPrint(); // fetch 함수를 실행시키고 다시 이 자리로 돌아옴
console.log(3); // 3
console.log(4); // 4
console.log(5); // 5
console.log(6); // 6 -> 바깥 코드가 다 실행되고 난 후 async 함수로 돌아가 await문에 있던 promise 객체가 fulfilled 상태가 될 때까지 기다린다.
// 더 이상 실행될 코드 없음
```
