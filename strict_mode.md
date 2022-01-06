# strict mode(엄격 모드)  
: strict mode는 자바 스크립트 언어의 문법을 더 엄격히 적용하여 명시적인 에러를 발생시킨다.  
따라서 오류를 줄여 안정적인 코드를 작성할 수 있다.  
- 적용 : 전역에 ```'use strict';```을 추가하면 스크립트 전체에 strict mode가 적용된다.  
함수 단위로도 사용이 가능하나 함수에 일일이 strict mode를 적용하는 것은 번거로운 일이니 지양하자.  
```javascript  
// strict mode가 아닌 경우
function foo (){
  x = 10; // 문제점 : 변수 키워드 미사용
}
foo(); 
console.log(x); // 10 -> 변수가 제대로 선언되지 않아도 값이 출력된다.

// 'use strict'; 사용시 ReferenceError가 난다.
```  

