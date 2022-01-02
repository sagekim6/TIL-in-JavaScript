# 배열 API's  
### join() : 배열을 문자열로 변환  
```javascript  
const num = [1, 2, 3];
const ArrToStr = num.join();
console.log(ArrToStr); // 1,2,3 -> 콤마를 자동으로 구분자로 사용한다.

const ArrToStr2 = num.join('and'); // 구분자를 지정해줄 수 있다
console.log(ArrToStr2); // 1and2and3
```  
### split() : 문자열을 배열로 변환한다.  
```javascript  
const str = '1, 2, 3';
const strToArr = str.split(','); // (필수)구분자를 문자열로 넣어 전달한다.
console.log(strToArr); // ['1', ' 2', ' 3']
```  
### reverse() : 요소의 순서를 거꾸로 만들어 준다.
```javascript  
const arrNum = [1, 2, 3, 4, 5];
const result = arrNum.reverse();

console.log(result); // [5, 4, 3, 2, 1]
console.log(arrNum); // [5, 4, 3, 2, 1] -> 원본 배열 자체를 바꾼다.
```  
###  slice() : 배열의 특정 부분을 잘라내어 새로운 배열로 만들어 리턴한다.  
```javascript  
const arr5 = ['a', 'b', 'c', 'd', 'e'];
const result2 = arr5.slice(2, 5); // (시작인덱스, 마지막인덱스) -> 마지막 인덱스는 자기자신을 포함하지 않는다.
console.log(result2); // ['c', 'd', 'e'] -> 새로운 배열을 만들어 리턴한다.
```  
