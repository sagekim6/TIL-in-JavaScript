# 재귀함수(recursive function)

- 자기 자신을 호출하는 함수로 종료조건에 만족하면 종료한다.
- 재귀함수는 호출될 때마다 메모리의 스텍에 쌓이게 된다. -> 종료조건을 잊지말고 작성해주어야한다.

```javascript
let x = 0;
function recur(x) {
  if (x < 0) {
    // <- 종료조건
    return console.log("end");
  }
  console.log(x--);
  recur(x);
}
recur(5);
// 5
// 4
// 3
// 2
// 1
// 0
// end
```

- 재귀함수로 작성가능한 문장은 for문이나 while문같은 반복문으로도 작성가능하다.

```javascript
for (let i = 5; i >= 0; i--) {
  console.log(i);
}
console.log("end");
```
