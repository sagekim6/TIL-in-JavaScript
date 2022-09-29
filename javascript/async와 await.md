# async와 await

<b>async/await 구문을 쓰는 이유는</b>

1. 개발자가 더 편하게 작성할 수 있도록 하고
2. 코드의 가독성을 높이기 위해  
   -> Promise 객체를 사용할 때, then 메소드를 사용하지 않고도 마치 동기 실행 코드처럼 코드를 훨씬 더 간단하고 편하게 작성할 수 있다.

## async

- 함수의 function 키워드 앞에 위치한다. -> 해당 함수안에 비동기적으로 실행되는 코드가 있다고 알려주는 의미
- async가 붙은 해당 함수는 <u>항상 프로미스를 반환</u>한다. 프로미스가 아닌 값이라도 프로미스 상태로 감싼 후 리턴한다.

## await

- async가 붙은 함수 안에서만 동작한다.(일반 함수 안에서 사용하면 에러가 발생한다.)
- await 키워드를 만나면 프로미스가 처리될 때까지 기다렸다가 그 결과를 반환한다.

```javascript
// 일반 프로미스 체이닝
fetch("http://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((result) => {
    console.log(result);
  });
```

```javascript
// 위의 fetch 함수 코드를 async와 await을 이용해 작성함
async function fetchAndPrint() {
  // fetch 함수가 fulfilled 상태가 될 때까지 기다렸다가 작업 성공 결과가 담긴 response 객체를 리턴한다.
  const response = await fetch("http://jsonplaceholder.typicode.com/users");
  const result = await response.json(); // response의 실제 내용이 변수 result에 담긴다.
  console.log(result);
}

fetchAndPrint();
```

### 실행 순서

- async 함수 안의 코드가 실행되다가 await을 만나면 일단 await 뒤의 코드가 실행된다.  
  그리고 <u>async 함수 바깥으로 나가서 나머지 코드를 실행한다.</u>

```javascript
async function fetchAndPrint() {
  console.log(2); // 2
  // fetch 함수를 실행 시키고 다시 함수가 실행된 지점으로 돌아간다.
  const response = await fetch("http://jsonplaceholder.typicode.com/users");
  console.log(7); // 7
  // response.json()을 먼저 실행시키고 다시 실행 흐름은 async 함수 바깥으로 나가게된다.
  const result = await response.json();
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

## try-catch문 사용

- async/await구문에서는 try-catch문으로 rejected상태가 되었을 때 에러를 대비할 수 있다.

```javascript
async function trycatch() {
  try {
    // 잘못된 URL
    const response = await fetch(
      "http://jsonplaceholder.typicode.commmmmmmm/users"
    );
    const result = await response.json();
    console.log(result);
  } catch (error) {
    console.log(error); // TypeError: Failed to fetch
  } finally {
    // 항상 실행된다.
    console.log("exit");
  }
}

trycatch();
```

## async 함수 안에서의 aysnc 함수 사용

- async 함수는 결국 Promise 객체를 리턴하기 때문에 await을 붙여서 사용가능하다.

```javascript
// 사용자의 민감한 정보를 제외하는 async 함수
const applyPrivacyRule = async function (users) {
  const resultWithRuleApplied = users.map((user) => {
    const keys = Object.keys(user); // Object.keys() : 객체의 key값만 묶어서 배열로 반환한다.
    const userWithoutPrvateInfo = {};

    // 주소와 전화번호 제외
    keys.forEach((key) => {
      if (key !== "address" && key !== "phone") {
        userWithoutPrvateInfo[key] = user[key];
      }
    });
    return userWithoutPrvateInfo;
  }); // End of forEach

  // 좀 더 오래 동작하는 함수로 만듬
  const p = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(resultWithRuleApplied);
    }, 2000);
  });
  return p;
};

async function getUsers() {
  try {
    const response = await fetch("http://jsonplaceholder.typicode.com/users");
    const users = await response.json();
    const resultWithPrivacyRuleApplied = await applyPrivacyRule(users); // aysnc 함수호출
    return resultWithPrivacyRuleApplied;
  } catch (error) {
    console.log(error);
  } finally {
    console.log("exit");
  }
}

getUsers().then((result) => {
  console.log(result);
});
```

### <async/await을 사용할 때 주의점>

- async 함수 안에서 무언가 반복하는 작업을 할 때는 주의를 해야한다. 왜냐하면 의도치 않게 순차적으로 실행되는 코드를 작성할 수도 있다.  
  -> 순차적인 처리가 필요한 경우가 아니라면 각 작업을 다시 async 함수로 묶어주면 된다.

```javascript
async function getResponses(urls) {
  // 이전 url에 리퀘스트를 보내고 리스폰스를 받고 출력하는것 까지 해야지 다음 url로 리퀘스트를 보낼 수 있다.
  for (const url of urls) {
    const response = await fetch(url);
    console.log(await response.text());
  }
}
// 순차적인 처리를 한다면 이 방법이 맞지만 순서 상관없이 결과만 잘 출력되기만 한다면 성능면에서 아쉬운 코드가 된다.
```

즉시 실행되는 aysnc 함수로 묶어 주면 각 URL에 대해서 fetch 함수를 실행해서 리퀘스트를 보내는 것을 순서대로 바로 실행해버린다.

```javascript
async function fetchUrls(urls) {
  for (const url of urls) {
    // 즉시 실행 함수에 aysnc로 만듬
    (async () => {
      const response = await fetch(url);
      console.log(await response.text());
    })();
  }
}
```
