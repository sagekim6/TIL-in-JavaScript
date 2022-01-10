# DOM요소선택  
### querySelector  
- css선택자를 만족하는 첫번째 요소를 반환한다.  
- 소괄호()안에 css선택자를 넣어주어야한다.  
```javascript  
const container = document.querySelector('.container'); 
const heading = document.querySelector('.heading');
console.log(heading); // null -> 일치하는 요소가 없으면 null을 반환한다.

const items = document.querySelectorAll('li'); // 모든 요소가 필요하면 querySelectorAll을 사용
console.log(items);
```  
### getElementBy  
- html요소를 선택하여 반환한다.  
```javascript  
// getElementById : id명으로 요소 선택
const heading = document.getElementById('heading'); // id이름이 heading인 요소 선택
console.log(heading);

// getElementByClassName : class명으로 요소 선택
const ol = document.getElementsByClassName('items'); // class이름이 items인 요소를 선택
console.log(ol);

// getElementsByTagName : 태그명으로 요소 선택
const tagName = document.getElementsByTagName('h1'); // h1태그 이름으로 요소 선택
console.log(tagName);                                // h1태그가 여러개라면 전부 선택된다.
```  
