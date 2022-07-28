  # for...in 반복문
  - <b>객체</b> 안에 있는 프로퍼티들로 반복적인 동작을 수행할 때 사용
  ```javascript
  // 기본 문법
  for (변수 in 객체) {
    //동작
  }
 ```  
 ```javascript
   const person = {
    name: "sese",
    age: 32,
    isVeryNice: true,
  };

  for (let key in person) {
    console.log(person[key]); // 대괄호 표기법을 통해 프로퍼티 값에도 접근할 수 있다.
  } // 객체의 프로퍼티 값을 하나하나 출력하는 for...in문 작성
  ```
 # for...of 반복문
 - <b>배열</b> 안에 있는 요소들을 순환한여 반복적인 동작을 수행한다.
 ```javascript
 // 기본 문법(for...in문과 비슷하다)
   for (변수 of 배열) {
    //동작
  }
 ```
 ```javascript
 let numbers = [1, 2, 3, 4, 5];
 
 for(let number of numbers){
 console.log(number); // 배열의 요소를 하나하나 출력하는 for...of문 작성
 }
 ```
