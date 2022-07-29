# 모듈화(Modularization)

- ES5에 추가되었다
- 많은 코드가 필요한 프로그램은 하나의 js파일로 관리하기보다 각 기능별로 여러개의 파일로 분리해서 관리하는 것이 좋다.  
  -> 이 과정을 모듈화, 이때 나온 파일 하나하나를 모듈이라고 한다
- 코드를 효율적으로 관리할 수 있고 다른 프로그램에서 재사용할 수 있다

### 모듈파일의 조건

- 모듈이 되는 파일은 모듈파일만의 독립적인 스코프를 가져야한다 -> 모듈 스코프(Module Scope)  
  -> 모듈파일 안에서 선언한 변수나 함수는 모듈파일 안에서만 사용가능해야한다
- js에 모듈스코프 추가: `type="module"`  
  -> type 속성을 지정해주면 모듈 스코프를 가지게되고 다른 외부 파일과 스코프를 공유하지 않게된다
- 브라우저에서 html파일을 불러오는 것이 아니라 서버를 통해 실행해야 에러가 나지 않는다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>모듈화</title>
  </head>
  <body>
    <!-- type 속성 추가 -->
    <script type="module" src="main.js"></script>
    <!-- <script type="module" src="printer.js"></script> 
        printer.js 파일은 모듈문법을 통해 내보내서 main.js 파일에서 받는다
        그렇기 때문에 html 파일에 굳이 script 가 작성될 필요가 없다
        -> 자바스크립트의 진입점 역할을 하는 파일 하나만 불러오면 된다.
    -->
  </body>
</html>
```

### 모듈의 필요성

- printer.js 파일에 선언된 title 변수에 재할당된다.  
  -> printer.js 파일의 변수가 main.js 파일에서 사용되었다. (나중에 문제가 될 가능성이 높다)

```javascript
// printer.js 파일
const title = "printer.js 파일";

function print(value) {
  console.log(value);
}
```

```javascript
// main.js 파일

title = "main.js 파일";
console.log(title); // -> 'main.js 파일'
```

---

- `type="module"` 속성을 지정해서 모듈 스코프를 갖게 만든 다음  
   공유하고 싶은 함수나 변수 앞에 `export` 키워드를 붙여주고 `import` 키워드로 받아서 사용가능하다.

```javascript
// printer.js 파일
export const title = "printer.js 파일";

export function print(value) {
  console.log(value);
}
```

```javascript
// main.js 파일

import { title, print } from "./printer.js";

console.log(title); // 'printer.js 파일'
print(title); // 'printer.js 파일'
```

### 이름 바꾸기

- 파일 안에서 title 변수가 필요한 경우가 생긴다면 as 키워드를 통해 바꿔줄 수 있다
- `{모듈파일에서 가져오는 이름 as 새로운 이름}`

```javascript
import { title as printerTitle, print } from "./printer.js";

const title = "main.js 파일";
console.log(title); // 'main.js 파일'
print(title); // 'main.js 파일'
```

### 한꺼번에 다루기

- \*(와일드카드 문자)로 작성하고 `as` 키워드로 이름을 지정해주면 객체처럼 접근해서 사용가능하다.
- import하는 파일에 `{}` 중괄호로 묶어서 한꺼번에 export할수 있다.
- 변수나 함수이름을 통해 여러값을 내보내는 것을 named export라고 부른다.

```javascript
const title = "printer.js 파일";

function print(value) {
  console.log(value);
}

// export하는 곳에서 바로 이름을 바꿀 수도 있다
export { title, print as printValue };
```

```javascript
// *(와일드카드 문자)를 사용해서 변수나 함수를 전부 불러올 수 있다
import * as printerJS from "./printer.js";

console.log(printerJS.title); // printer.js 파일
```

### default export

- default 키워드가 붙으면 하나의 대상만 내보낸다
- 변수나 함수이름을 export하는 것 뿐만아니라 값 하나를 전달할 수도 있다  
  -> default 키워드는 모듈 파일에서 딱 하나만 사용할 수 있다.

```javascript
// printer.js 파일
const members = [
  { name: "sage", age: 26 },
  { name: "jane", age: 30 },
  { name: "sese", age: 17 },
];
export default members;
```

```javascript
// main.js 파일에서 import하기

// {default as 새로운 이름} 부분을 생략 가능하다
import { default as printerMembers } from "./printer.js";
console.log(printerMembers[0].name); // sage

// default export와 named export를 같이 작성해도 되지만
// 가독성이 떨어지므로 둘 중 하나의 방식을선택해서 사용하는 것을 권장한다
```
