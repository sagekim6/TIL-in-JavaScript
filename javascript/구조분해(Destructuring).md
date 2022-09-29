# 구조분해 (Destructuring)

- 배열이나 객체의 구조를 분해하는 문법
- 인덱스가 붙는 배열과 프로퍼티에 이름이 붙는 객체는 서로 구조가 다르기 때문에 구조분해도 적용되는 방식에 차이가 있다.

### 1. 배열 구조분해

- 배열 이외의 값을 할당하면 에러가 나기 때문에 주의해야한다
- 배열의 값이 변수에 순서대로 할당된다

```javascript
const rank = ["A", "B", "C", "D"];

// const macbook = rank[0];
// const ipad = rank[1];
// const airpods = rank[2];
// const coupon = rank[3];
const [macbook, ipad, airpods, coupon] = rank; // 위에 작성한 코드와 똑같이 작동한다
// 할당 연산자(=) 왼편에 변수의 이름이 배열의 형태로 선언되어있고 rank 배열 자체를 할당한다

console.log(macbook, ipad, airpods, coupon); // A B C D
```

#### 선언된 변수의 개수와 배열의 길이를 맞출 필요는 없다

- 인덱스에 따라 순서대로 할당되기 때문에 남는 요소는 어느 변수에도 할당되지 않는다
- 변수들 보다 배열의 요소가 적은 경우 할당받지 못한 변수는 undefined가 할당된다

```javascript
const rank = ["A", "B", "C", "D", "E", "F"];

const [macbook, ipad, airpods, coupon] = rank;
console.log(macbook, ipad, airpods, coupon); // A B C D
```

```javascript
const rank = ["A", "B", "C"]; // 3개

const [macbook, ipad, airpods, coupon] = rank;
console.log(macbook, ipad, airpods, coupon); // A B C undefined
```

#### rest 파라미터를 사용

- rest 파라미터를 사용하여 나머지 요소를 배열로 만들어 리턴할 수 있다. 단, rest 파라미터는 제일 마지막에 작성해준다

```javascript
const rank = ["A", "B", "C", "D", "E", "F"];

const [macbook, ipad, airpods, ...coupon] = rank;
console.log(macbook, ipad, airpods, coupon); // A B C (3) ['D', 'E', 'F']
```

#### 기본값 지정과 변수에 할당된 값 교환하기

```javascript
const rank = ["A", "B", "C"]; // 3개

// 기본값을 지정해줄 수 있다.
const [macbook, ipad, airpods, coupon = "none"] = rank;
console.log(macbook, ipad, airpods, coupon); // A B C none
```

```javascript
let macbook = "A";
let ipad = "B";

console.log(macbook); // 'A'
console.log(ipad); // 'B'

// 구조분해를 활용해 변수에 할당된 값을 교환
[macbook, ipad] = [ipad, macbook];

console.log(macbook); // 'B'
console.log(ipad); // 'A'
```

### 2. 객체 구조분해

- 배열을 분해할 때는 대괄호로 감쌌던 것처럼 객체를 분해할 때는 중괄호로 변수를 감싸준다.
- 중괄호 안에 있는 변수명과 할당된 객체의 프로퍼티 이름이 똑같다면 중괄호안에 있는 변수에 프로퍼티가 할당되는 방식으로 동작한다.

```javascript
const macbook = {
  title: "맥북 프로 16인치",
  price: 3690000,
  memory: "16 GB",
  storage: "1TB SSD 저장 장치",
  display: "16형 Retina 디스플레이",
};

// const title = macbook.title;
// const price = macbook.price;
const { title, price } = macbook; // 위에 작성한 코드와 똑같이 동작한다

console.log(title, price); // 맥북 프로 16인치 3690000
```

#### 존재하지 않는 프로퍼티라면 undefined

```javascript
const macbook = {
  title: "맥북 프로 16인치",
  price: 3690000,
  memory: "16 GB",
  storage: "1TB SSD 저장 장치",
  display: "16형 Retina 디스플레이",
};
// 객체에 존재하지 않은 프로퍼티 이름이라면 undefined로 나온다
const { title, color } = macbook;

console.log(title, color); // 맥북 프로 16인치 undefined
```

#### 기본값 지정하기 & rest 파라미터 사용

```javascript
const macbook = {
  title: "맥북 프로 16인치",
  price: 3690000,
  memory: "16 GB",
  storage: "1TB SSD 저장 장치",
  display: "16형 Retina 디스플레이",
};
// 기본값을 지정해줄 수도 있다
const { title, color = "silver" } = macbook;

console.log(title, color); // 맥북 프로 16인치 silver
```

```javascript
const macbook = {
  title: "맥북 프로 16인치",
  price: 3690000,
  memory: "16 GB",
  storage: "1TB SSD 저장 장치",
  display: "16형 Retina 디스플레이",
};
// rest 파라미터를 사용해서 남은 프로퍼티를 객체로 변수에 할당할 수 있다
const { title, ...rest } = macbook;

console.log(title); // 맥북 프로 16인치
console.log(rest);
// {price: 3690000, memory: '16 GB', storage: '1TB SSD 저장 장치', display: '16형 Retina 디스플레이'}
```

#### 변수명 바꾸기

- 위의 방법은 변수명과 프로퍼티 이름이 동일해야 했지만 변수명을 다르게 지정할 수도 있다.
- 객체 내부의 프로퍼티 이름을 변수명으로 사용할 수 없을 때 유용하다.
- {프로퍼티 이름: 원하는 변수명}의 방식으로 이름을 바꿔줄 수 있다.

```javascript
const macbook = {
  title: "맥북 프로 16인치",
  price: 3690000,
  memory: "16 GB",
  storage: "1TB SSD 저장 장치",
  display: "16형 Retina 디스플레이",
};
// {프로퍼티 이름: 변수명}
const { title: product, price: sale } = macbook;

console.log(product); // 맥북 프로 16인치 -> 콘솔에 잘 출력된다
console.log(sale); // 3690000
```

### 3. 구조분해 활용

#### 함수의 리턴값이 배열일 때

```javascript
function getArr() {
  return ["A", "B", "C"];
}

const [a1, a2, a3] = getArr();
console.log(a1); // A
console.log(a2); // B
console.log(a3); // C
```

#### 함수의 파라미터로 구조분해 변수 할당하기

```javascript
function printWinner([macbook, ipad, airpods, ...coupon]) {
  console.log(`맥북: ${macbook}`);
  console.log(`아이패드: ${ipad}`);
  console.log(`에어팟: ${airpods}`);
  for (let user of coupon) {
    console.log(`쿠폰: ${user}`);
  }
}
// 배열을 선언해서 인수로 넘겨준다
const rank = ["사람A", "사람B", "사람C", "사람D", "사람E"];
printWinner(rank);
// 맥북: 사람A
// 아이패드: 사람B
// 에어팟: 사람C
// 쿠폰: 사람D
// 쿠폰: 사람E
```

```javascript
const person = {
  name: "Sage",
  age: 26,
  isMarried: false,
};

function printPersonInfo({ name, age, isMarried }) {
  console.log(name, age, isMarried);
}
printPersonInfo(person); // Sage 26 false
```
