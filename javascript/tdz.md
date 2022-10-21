# 일시적 사각지대(Temporal Dead Zone: TDZ)

## 호이스팅(Hoisting)

- 호이스팅은 변수나 함수가 선언된 위치와는 상관없이 최상단에 위치한 것처럼 동일 스코프에서는 어디서든 참조할 수 있는 것을 말한다.

```javascript
var x = "outer scope";
(function () {
  console.log(x); // undefined
  var x = "inner scope";
})();
```

스코프안에서 선언된 변수는 항상 최상위에서 선언한 것처럼 동작한다. 그래서 위의 예제는

```javascript
var x = "outer scope";
(function () {
  var x;

  console.log(x); // undefined
  x = "inner scope";
})();
```

이렇게 선언된 것과 같다. `var` 키워드는 선언과 동시에 초기화가 되기 때문에 에러가 나는 것이 아니라 `undefined`가 출력된다.

## 일시적 사각지대(Temporal Dead Zone: TDZ)

- `let`, `const` 키워드는 `TDZ`의 제약을 받는다. 즉, 변수가 초기화 되기 전에 참조를 하려고 하면 `ReferenceError`가 난다.
  - 코드를 예측가능하게 하고 잔재적인 버그를 쉽게 찾아낼 수 있다.

```javascript
const x = "outer scope";
(function () {
  console.log(x); // ReferenceError
  const x = "inner scope";
})();
```

- `let`, `const` 키워드는 호이스팅이 된다. 그래서 선언은 되었지만 값이 초기화 되지 않았다는 `ReferenceError`가 나는 것이다.  
  만약 호이스팅이 되지 않았다면 변수가 정의되지 않았다는 식의 에러가 났을 것이다.
