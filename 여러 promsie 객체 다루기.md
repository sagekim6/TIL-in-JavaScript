# 여러 promsie 객체 다루기

## 1. all 메소드

- all 메소드는 여러 Promise 객체의 작업 성공 결과를 기다렸다가 모두 한 번에 취합하기 위해서 사용
- all 메소드도 then 메소드처럼 <u>새로운 Promise 객체를 리턴</u>한다.
- promise 객체가 담긴 배열이 인자로 넘어가고 배열 안에 있는 <b>모든 Promise 객체가 pending에서 fulfilled 상태가 될 때까지 대기한다.</b>  
  그리고 모든 Promise 객체들이 fulfilled 상태가 되면, all 메소드가 리턴할 Promise 객체는 fulfilled 상태가 되고,  
  각 Promise 객체의 작업 성공 결과들로 이루어진 배열을, 그 작업 성공 결과로 갖게 됩니다.
- 배열로 넘어간 Promise 객체 중 <b>하나라도 rejected 상태가 되면</b>, 전체 작업이 실패한 것으로 간주된다. -> catch 사용

```javascript
// fulfilled 상태인 promise 객체
const res1 = Promise.resolve("resolved1!");
const res2 = Promise.resolve("resolved2!");

// all 메소드의 인자로 배열을 넣어준다.
// -> res1과 res2 둘 다 fulfilled상태이기 때문에 all 메소드는 fulfilled 상태인 promise 객체를 리턴한다.
Promise.all([res1, res2])
  .then((result) => {
    console.log(result[0]); // resolved1!
    console.log(result[1]); // resolved2!
  })
  .catch((error) => {
    console.log(error);
  });
```

## 2. race 메소드

- 여러 promise 객체가 있는 배열을 인자로 받고 promise 객체를 리턴한다.
- 인자로 들어온 배열의 여러 Promise 객체들 중에서 가장 먼저 fulfilled 상태 또는 rejected 상태가 된 Promise 객체와 동일한 상태와 결과를 갖게된다.

```javascript
const p1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success"), 1000);
});
const p2 = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error("fail")), 2000);
});
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error("fail2")), 4000);
});

Promise.race([p1, p2, p3])
  .then((result) => {
    console.log(result);
  })
  .catch((value) => {
    console.log(value);
  });
```

## 3. allSetteled 메소드

- all 메소드와 비슷하게 promise 객체를 리턴하고 배열을 인자로 받는다.  
  그러나 allSetteled 메소드는 이름 그대로 배열에 담긴 promise 객체가 setteled 상태가 되기만 하면된다.
- 배열에 작업 결과를 담아 리턴한다.

## 4. any 메소드

- 인자로 받은 여러 Promise 객체들 중에서 가장 먼저 fulfilled 상태가 된 Promise 객체의 상태와 결과값을 리턴합니다.
- 모든 promise 객체가 rejected 상태가 되면 AggregateError라고 하는 에러를 작업 실패 정보로 갖고 rejected 상태가 된다.
