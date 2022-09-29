# JSON

- HTTP통신을 위한 데이터 포맷이다.
- 대부분의 프로그래밍 언어에서 사용가능하다.
- 객체와 유사하게 키와 값으로 구성되어 있으며 키는 반드시 큰따옴표("")로 묶어야 한다.

### JSON.stringify : 객체를 JSON으로 변환.

- 직렬화 : 객체를 문자열로 변환하는 것.
- 들어갈 수 있는 인수 : `JSON.stringify(obj, ?replacer, ?space)`

```javascript
const person = {
  name: "sage", // 일반 객체에서는 작은 따옴표('') 사용 가능
  age: 4,
  alive: true,
  hobby: ["cooking", "tennis"], // 배열도 문자열로 변환한다.
};

// 1. 객체를 json 포맷 문자열로 변환 -> stringify(obj)
const json4 = JSON.stringify(person);
console.log(typeof json4, json4);
// string {"name":"sage","age":4,"alive":true,"hobby":["cooking","tennis"]}

// 2. 들여쓰기 적용
const prettyJson = JSON.stringify(person, null, 2);
console.log(typeof prettyJson, prettyJson);
// string {
//   "name": "sage", // 큰 따옴표로 변환되어 출력된다.
//   "age": 4,
//   "alive": true,
//   "hobby": [
//     "cooking",
//     "tennis"
//   ]
// }

function filter(key, value) {
  return typeof value === "number" ? undefined : value;
}

// 3. replacer :  속성을 선택할 수 있다
const filteredObj = JSON.stringify(person, filter, 2); // 숫자를 필터링해서 반환되지 않게 한다.
console.log(typeof filteredObj, filteredObj);
// string {
//   "name": "sage",
//   "alive": true,
//   "hobby": [
//     "cooking",
//     "tennis"
//   ]
// }
```

### JSON.parse : JSON을 객체로 변환

- 역직렬화 : JSON포맷의 문자열을 객체화 하는 것.

```javascript
const obj2 = {
  name: "lee",
  age: 20,
  hasJob: function () {
    console.log(`${this.name} has a job!`);
  },
};

const json5 = JSON.stringify(obj2, null, 2);
console.log(typeof json5, json5); // 심볼과 함수는 변환되지 않는다.
// string {
//   "name": "lee",
//   "age": 20
// }

const parsed = JSON.parse(json5); // json으로 변환된 문자열을 다시 객체로 변환했기 때문에 여전히 함수는 포함되지 않고 출력된다.
console.log(typeof parsed, parsed); // object {name: 'lee', age: 20}
```

#### 직렬화, 역직렬화 과정이 왜 필요한가?

- 자바스크립트 실행 환경에서만 인식되는 객체를 어느 환경에서든 해석될 수 있는 포맷으로 변환하기 위해 직렬화과정을 거친다.
- 문자열 타입을 객체로 변환해줘야 코드에서 자유롭게 사용할 수 있다.
