# Math 객체

## Math.abs()

- 파라미터로 넘어가는 숫자의 절대값을 리턴합니다.
- 절댓값은 어떤 값의 양수버전이다.

```javascript
console.log(Math.abs(-10)); // 10
console.log(Math.abs(10)); // 10
```

## Math.max()

- 파라미터로 넘겨진 수 중에 가장 큰 값을 리턴합니다

```javascript
console.log(Math.max(2, -1, 4, 5, 0)); // 5
```

## Math.min()

- 파라미터로 넘겨진 수 중에 가장 작은 값을 리턴합니다.

```javascript
console.log(Math.min(2, -1, 4, 5, 0)); // -1
```

## Math.pow(x, y)

- x의 y승의 결과값을 리턴한다.
- 제곱의 개념 : 2의 3승(혹은 2의 세제곱)은 2를 세 번 곱한다는 뜻이다.

```javascript
console.log(Math.pow(2, 3)); // 8
console.log(Math.pow(5, 2)); // 25
```

## Math.sqrt(x)

- x의 제곱근을 리턴합니다.
- 제곱근의 개념 : '제곱'의 반대라고 생각하면 된다. 5의 제곱이 25이기 때문에, 25의 제곱근은 5이다.

```javascript
console.log(Math.sqrt(25)); // 5
console.log(Math.sqrt(49)); // 7
```

## Math.round(x)

- x의 반올림된 값을 리턴합니다.
- 소수점 부분이 0.5 이상이면 가장 가까운 정숫값으로 올라가고, 소수점 부분이 0.5 미만이면 가장 가까운 정숫값으로 내려간다.

```javascript
console.log(Math.round(2.3)); // 2
console.log(Math.round(2.49)); // 2 -> 소수점과 가까운 수가 0.4이므로 수는 내려간다
console.log(Math.round(2.5)); // 3
```

## Math.floor(x)

- x의 버림값을 리턴한다.
- 소수 부분이 얼마인지 상관없이 소수점 부분을 버린다.

```javascript
console.log(Math.floor(2.4)); // 2
console.log(Math.floor(2.49)); // 2
console.log(Math.floor(2.8)); // 2
```

## Math.ceil(x)

- x의 올림값을 리턴한다.
- 소수 부분이 얼마인지 상광 없이 수를 올림한 후 리턴한다.

```javascript
console.log(Math.ceil(2.4)); // 3
console.log(Math.ceil(2.49)); // 3
console.log(Math.ceil(2.8)); // 3
```

## Math.random()

- 0 이상 1 미만의 값이 랜덤으로 리턴된다.

```javascript
console.log(Math.random()); // 0.9584323636273797
console.log(Math.floor(Math.random() * 5)); // 0에서 4까지 무작위로 숫자를 리턴함
console.log(Math.floor(Math.random() * 10)); // 0에서 9까지 무작위로 숫자를 리턴함
```
