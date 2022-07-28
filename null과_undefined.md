# typeof 연산자

- 해당 값이 어떤 자료형인지 알려준다.
- 사칙연산자보다 우선순위가 높다.

```javascript
{
  console.log(typeof 123); // number
  console.log(typeof "123"); // string
  console.log(typeof false); // boolean
  console.log(typeof [1, 2, 3]); // object -> 배열은 객체로 나온다

  function greeting() {
    return "Hello!";
  }
  console.log(typeof greeting); // function
```

```javascript
// typeof는 연산자 이기 때문에 앞에서부터 차례대로 연산한다.
console.log(typeof "Hello" + "World"); // stringWorld
// -> typeof 'Hello'는 string이다. 그리고 뒤에 따라나오는 'World'를 만나면서 stringWorld가 나오게 된다.
console.log(typeof 8 - 3); // NaN
// -> typeof 8은 number가 나오고 문자열 number와 숫자 3은 연산할 수 없으므로 NaN이 나온다.

// 괄호를 사용해 우선순위를 지정해준다.
console.log(typeof (8 - 3)); // number
```

# null과 undefined

### null(의도적인 없음) : 비어있는 값을 의도적으로 할당

### undefined(처음부터 없음) : 아무것도 존재하지 않음

```javascript
let sage;
console.log(sage); // undefined -> 초기화되지않은 변수를 콘솔에 찍으면 undefined가 나온다

sage = null; // 의도적으로 이 변수는 비어있다는 뜻
console.log(sage); // null
```

```javascript
console.log(null == undefined);
console.log(null === undefined); // undefined -> 둘은 다른 자료형이다.

let cup;
console.log(cup); // undefined
cup = "water";
console.log(cup); // water
cup = null;
console.log(cup); // null
```
