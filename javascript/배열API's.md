# 배열 API's

### join() : 배열을 문자열로 변환

```javascript
const num = [1, 2, 3];
const ArrToStr = num.join();
console.log(ArrToStr); // 1,2,3 -> 콤마를 자동으로 구분자로 사용한다.

const ArrToStr2 = num.join("and"); // 구분자를 지정해줄 수 있다
console.log(ArrToStr2); // 1and2and3
```

### split() : 문자열을 배열로 변환한다.

```javascript
const str = "1, 2, 3";
const strToArr = str.split(","); // (필수)구분자를 문자열로 넣어 전달한다.
console.log(strToArr); // ['1', ' 2', ' 3']
```

### reverse() : 요소의 순서를 거꾸로 만들어 준다.

```javascript
const arrNum = [1, 2, 3, 4, 5];
const result = arrNum.reverse();

console.log(result); // [5, 4, 3, 2, 1]
console.log(arrNum); // [5, 4, 3, 2, 1] -> 원본 배열 자체를 바꾼다.
```

### slice() : 배열의 특정 부분을 잘라내어 새로운 배열로 만들어 리턴한다.

```javascript
const arr5 = ["a", "b", "c", "d", "e"];
const result2 = arr5.slice(2, 5); // (시작인덱스, 마지막인덱스) -> 마지막 인덱스는 자기자신을 포함하지 않는다.
console.log(result2); // ['c', 'd', 'e'] -> 새로운 배열을 만들어 리턴한다.
```

---

```javascript
// 예제
class Student {
  constructor(name, age, enrolled, score) {
    this.name = name;
    this.age = age;
    this.enrolled = enrolled;
    this.score = score;
  }
}
const student = [
  new Student("A", 29, true, 45),
  new Student("B", 28, false, 80),
  new Student("C", 30, true, 90),
  new Student("D", 40, false, 66),
  new Student("E", 18, true, 88),
];
```

### find() : 전달된 콜백함수가 true인 첫번째 값을 리턴한다. 없다면 undefined를 리턴한다.

```javascript
// 점수가 90점인 학생 출력
const result3 = student.find((value) => value.score === 90);
console.log(result3); // Student {name: 'C', age: 30, enrolled: true, score: 90}
```

### filter() : 콜백함수에 부합한 값만 모아서 새로운 배열로 만들어 리턴한다.

```javascript
// enrolled가 true인 값을 출력
const result4 = student.filter((value) => value.enrolled);
console.log(result4);
```

### map() : 배열안에 있는 요소에 호출한 콜백함수의 결과를 모아 새로운 배열로 만들어 리턴한다.

```javascript
const result5 = student.map((value) => value.score); // 학생들의 점수만 출력
console.log(result5); // [45, 80, 90, 66, 88]

const result6 = student.map((value) => value.score * 2); // 점수를 두배로 만들기
console.log(result6); // [90, 160, 180, 132, 176] // 개발자가 원하는 값으로 변환할 수 있다.
```

### some() : 요소중에 하나라도 특정조건에 부합하면 true를 리턴한다.

```javascript
const result7 = student.some((student) => student.score < 50);
console.log(result7); // true
```

### every() : 모든 요소가 콜백함수의 조건에 부합하면 true를 리턴한다.

```javascript
const result8 = student.every((student) => student.score < 50);
console.log(result8); // false
```

### reduce() : 배열의 요소를 하나씩 돌면서 이전 콜백의 리턴값을 넘겨받아 작업을 수행한다.

- reduce(콜백함수(이전값, 현재값, ?현재값인덱스, ?배열)=>{실행문}, ?초기인덱스값);

```javascript
// 요소의 총합을 출력
const num9 = [1, 2, 3, 4, 5];
const r = num9.reduce((prevValue, currValue) => prevValue + currValue); // 초기값 지정X
console.log(r); // 15

class Person2 {
  constructor(name, age, isMarried) {
    this.name = name;
    this.age = age;
    this.isMarried = isMarried;
  }
}

const p1 = [
  new Person2("peter", 30, true),
  new Person2("sage", 25, false),
  new Person2("kim", 5, false),
];

const r2 = p1.reduce((prev, curr) => prev + curr.age, 0); // 초기 인덱스번호를 0으로 지정
console.log(r2); // 60
```
