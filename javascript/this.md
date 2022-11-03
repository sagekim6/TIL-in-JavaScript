# this 키워드

`this`는 자기 자신을 가리키는 자기 참조 변수다.

## `바인딩`이란?

- 식별자와 값을 연결하는 과정을 뜻한다. 구체적인 값, 성격을 확정짓는 것이다.
- this는 상황에 따라 가리키는 대상이 다르다.

## 함수 호출 방식에 따른 this 바인딩

- `this`는 **<u>함수가 호출될 때</u>** 값이 결정된다.

### 1. 일반 함수 호출 안에서 쓴 this

- 일반 함수로 호출된 모든 함수(중첩 합수, 콜백 함수 포함) 내부의 this에는 기본적으로 **전역 객체가 바인딩된다.**
- <u>엄격 모드가 적용되면</u> 일반 함수 내부에서의 this는 **undefined**가 된다.

```javascript
const foo = function () {
  console.log("foo의 this: ", this); // Window
  function bar() {
    console.log("bar의 this: ", this); // Window
  }
  bar();
};
foo();
```

### 2. 메소드 호출

- **메소드를 호출한 객체에 바인딩 된다.**
- 메소드는 다른 객체의 프로퍼티에 할당하거나 다른 객체의 메소드가 될 수 있다. 또한 변수에 할당하여 일반 함수로 호출될 수도 있다.

```javascript
const person1 = {
  name: "sage",
  getName() {
    return this.name;
  },
};

console.log(person1.getName()); // sage

const person2 = {
  name: "lee",
};

person2.getName = person1.getName; // -> getName메소드를 person2 객체의 메소드로 할당
console.log(person2.getName()); // lee
```

- **누가 `getName` 메소드를 호출했는지가 중요하다.** `person1` 객체가 호출하면 `this`는 `person1`객체에 바인딩 되고  
  `person2` 객체가 호출하면 `this`는 `person2` 객체에 바인딩 된다.
- 메소드를 변수에 담아 일반 함수로 호출 가능하다.
- 일반 함수로 호출하면 전역 객체가 되므로 `this.name`은 `Window.name`이 되므로 빈문자열이 출력된다.

```javascript
const getName = person1.getName;
console.log(getName()); // ''
```

### 3. 생성자 함수 호출

- 생성자 함수 내부의 this는 생성자 함수가 **생성할 인스턴스를 가리킨다.**

```javascript
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

const c1 = new Circle(5);
console.log(c1.getDiameter()); // 10

const c2 = new Circle(10);
console.log(c2.getDiameter()); // 20
```

### 4. `apply`/ `call`/ `bind` 메소드에 의한 간접 호출

#### `apply`와 `call` 메소드

- 첫번째로 전달하는 인자를 `this` 값으로 바인딩하고 함수를 실행한다.
- `apply` 메소드는 인자를 배열로 전달한다.

```javascript
function thisBinding() {
  console.log(arguments);
  return this;
}

// this로 사용할 객체
const thisArg = { x: 1 };
console.log(thisBinding()); // Window
```

- 첫 번째 인수로 전달한 특정 객체를 this에 바인딩한다.
- `apply` : 두 번째 인수는 배열로 묶어 전달한다.

```javascript
thisBinding.apply(thisArg, [1, 2, 3]);
// Arguments(3) [1, 2, 3, callee: ƒ, Symbol(Symbol.iterator): ƒ]
// {x: 1}
```

- 첫 번째 인수로 전달한 특정 객체를 this에 바인딩한다.
- `call` : 두 번째 인수는 쉼표로 구분해 전달한다.

```javascript
thisBinding.call(thisArg, 1, 2, 3);
// Arguments(3) [1, 2, 3, callee: ƒ, Symbol(Symbol.iterator): ƒ]
// {x: 1}
```

#### `bind` 메소드

- 함수를 호출하지 않고 `this`로 사용할 객체만 전달한다.
- 따라서 함수를 호출하려면 명시적으로 호출해야한다.

```javascript
function showThis() {
  return this;
}

// this로 사용할 객체
const arg = { a: 1 };

// bind는 함수를 호출하지 않는다.
showThis.bind(arg); // ƒ showThis(){}

// 따라서 명시적으로 호출해야 한다.
console.log(showThis.bind(arg)()); // {a: 1}
```

- this가 불일치 하는 문제를 해결하기 위해 bind가 사용된다.

```javascript
// 외부 콜백 함수와 내부 콜백 함수가 가리키는 객체가 서로 다른 문제가 생긴다
const p3 = {
  name: "sese",
  // 콜백 함수가 호출되기 전의 시점에 f메소드는 p3 객체를 가리킨다
  f(callback) {
    setTimeout(callback, 100);
  },
};

// 일반 함수로 호출된 콜백 함수는 전역 객체를 가리킨다
p3.f(() => {
  console.log(`Hi! My name is ${this.name}.`); // Hi! My name is .
});
```

```javascript
const p3 = {
  name: "sese",
  f(callback) {
    setTimeout(callback.bind(this), 100); // bind 메소드를 사용해서 외부, 내부 this를 일치시킨다.
  },
};

p3.f(function () {
  console.log(`Hi! My name is ${this.name}.`); // Hi! My name is sese.
});
```

## 화살표 함수와 `this` 바인딩
