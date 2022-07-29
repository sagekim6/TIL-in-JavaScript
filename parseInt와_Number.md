# `parseInt` VS `Number`

문자열을 숫지로 형변환해준다는 공통점이 있다.

## `parseInt(str)`

인자로 넘겨진 문자열을 숫자로 형변환한다.

```javascript
console.log(parseInt("12345")); //12345
```

- 문자열이 숫자로 시작하는 경우: 숫자가 끝날 때까지만 형변환한다.

```javascript
// 숫지로 먼저 시작하고 숫자부분만 형변환된다.
const num = parseInt("26살");
console.log(num); // 26
```

- 문자열이 문자로 시작하는 경우: 형변환되지 않는다. &rarr; `NaN`

```javascript
// 문자로 먼저 시작하고 형변환되지 않아 NaN가 콘솔에 찍힌다.
const num = parseInt("나이: 26살");
console.log(num); // NaN
```

- 소수점 변환: 소수점은 떼버리고 정수만 변환된다.

```javascript
const num = parseInt("3.14");
console.log(num); // 3
```

## `Number(str)`

인자로 넘겨진 문자열을 숫자로 형변환한다.

```javascript
console.log(Number("12345")); //12345
```

- 문자열이 숫자가 아닐경우 형변환되지 않는다.

```javascript
// 26은 숫자지만 문자열이 포함되어 있기 때문에 형변환되지 않는다.
const num = Number("26살");
console.log(num); // NaN
```

- 소수점 변환: 소수점까지 전부 형변환 해준다.

```javascript
const num = Number("3.14");
console.log(num); // 3.14
```
