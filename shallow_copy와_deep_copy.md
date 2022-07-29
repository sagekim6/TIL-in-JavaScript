# 얕은 복사(shallow copy)와 깊은 복사(deep copy)

얕은 복사는 객체의 참조값을 복사하고 깊은 복사는 객체의 실제 값을 복사하는 차이가 있다.

## 원시값의 복사

- 원시값(primitive)에는 string, number, null, undefined, boolean, bigint, symbol이 있고 불변성을 가진다.
- 변수에 원시값을 저장하면 메모리에 원시값 자체가 담기게 된다.

```javascript
let x = 1;
let y = x;

console.log(y); // 1

x = 2;

console.log(y); // 1 -> y의 값은 그대로!
```

- y는 x의 실제 값자체를 할당 받았다. 그래서 x의 값이 변경되더라도 y는 아무런 영향을 받지 않는다.  
  **이처럼 실제 값을 복사하는 것을 깊은 복사라고 한다.**

## 참조값의 복사

- 참조값에는 객체(object)가 있고 참조값은 실제 값이 아닌 값이 있는 곳의 주소값을 변수가 참조한다.

```javascript
const obj = {
  num: 1,
};

const objCopy = obj;

console.log(objCopy.num); // 1

obj.num = 2;

console.log(objCopy.num); // 2
```

- obj를 objCopy에 할당하게 되면 objCopy는 obj의 값이 아닌 값이 있는 주소값을 할당받게 된다.  
  결국 둘은 같은 데이터를 공유하는 것이기 때문에 obj의 값이 바뀌면 objCopy의 값도 바뀌게 된다.
- 이처럼 객체의 객체의 **실제값이 아닌 참조값을 복사하는 것을 얕은 복사라고 한다.**

### 객체 깊은 복사하기

`JSON.parse()`는 문자열을 객체로 변환하고 `JSON.stringify()`는 객체를 문자열로 변환시킨다.  
`stringify()`를 사용하는 과정에서 원본 객체와의 참고가 사라집니다. (아마도 참조형을 원시형으로 만들기 때문에?)  
그리고 `parse()`를 사용해 다시 문자열을 객체로 만드는 방식으로 객체의 깊은 복사를 구현할 수 있다.

```javascript
const obj = {
  num: 1,
};

const deepCopy = JSON.parse(JSON.stringify(obj));

console.log(deepCopy.num); // 1

obj.num = 2;

console.log(deepCopy.num); // 1 -> 원본 객체의 값이 달라져도 값이 바뀌지 않는다.
```
