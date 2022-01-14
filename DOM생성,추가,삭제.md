# 노드 생성과 추가 및 삭제  
```html  
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DeepDive</title>
    <script defer src="39장.js"></script>
    <style></style>
  </head>
  <body>
    <div class="container">
      <h1 id="heading">heading1</h1>
      <p class="content">
        Lorem ipsum dolor sit amet, consect etur adipisicing elit. Laudantium,
        maxime adipisci saepe sequi aliquam dolorum laborum, nemo eloxpedita
        aperiam suscipit nostrum consequatur dolorem repellendus recusandae
        quasi mollitia esse animi iusto.
      </p>
      <ol class="items">
        <li><a href="#">a</a></li>
        <li><a href="#">b</a></li>
        <li><a href="#">c</a></li>
      </ol>
    </div>
  </body>
</html>
```  
#### 1. createElement('태그명');  
- 요소 노드를 생성한다.
- 요소 노드를 생성만 할 뿐 DOM에는 추가하지 않는다.  
```javascript  
// 요소 노드 선택
const $items = document.querySelector('.items');

// 요소 노드 생성
const $li = document.createElement('li'); // li생성
```  
#### 2. createTextNode('문자열');  
- 텍스트 노드를 생성하여 반환한다.  
- 텍스트 노드를 생성할 뿐 요소 노드에 추가하지는 않는다.->요소 노드에 추가하는 처리가 별도로 필요  
```javascript  
const txtNode = document.createTextNode('d');
```  
#### 3. appendChild(자식 노드);  
- 인수로 전달받은 노드를 마지막 자식 노드로 DOM에 추가한다.  
- 노드를 추가할 위치는 지정할 수 없고 마지막 자식 노드로 추가된다.  
```javascript  
// 생성한 li요소 노드와 텍스트 노드 연결
$li.appendChild(txtNode);

// li 요소를 items 요소의 마지막 자식 노드로 추가->DOM에 연결
$items.appendChild($li);
// DOM에 추가가 되어야 리플로우와 리페인팅이 실행된다.(화면에 나타난다)
```  
#### 4. 노드를 여러 개 생성하고 추가하기  
- 방법 1 :  컨테이너 요소 사용->DOM을 변경하는 횟수를 줄일 수 있다(성능에 유리).  
- 단점 : 불필요한 컨테이너 요소(div)가 추가 된다.  
```javascript  
// 컨테이너 요소 노드 생성
const $container = document.createElement('div');

// forEach문 사용
['e', 'f', 'g'].forEach(txt=>{
  // 1. 요소 노드 생성
  const $li = document.createElement('li');
  // 2. 텍스트 노드 생성
  const txtNode = document.createTextNode(txt);
  
  // 3. 텍스트 노드와 li 연결
  $li.appendChild(txtNode);
  // 4. 연결한 li를 컨테이너에 연결
  $container.appendChild($li);
});
// 5. 연결한 컨테이너 요소 노드를 $items에 연결
$items.appendChild($container);
```  
- 방법 2 : DocumentFragment 사용(권장)  
  - 노드 객체의 일종으로 부모 노드가 없어서 기존 DOM과는 별도 로 존재한다.  
  - DocumentFragment 노드를 DOM에추가하면 자신은 제거되고 자식 노드만 추가된다.  
```javascript  
// DocumentFragment 노드 생성
const $fragment = document.createDocumentFragment();

// forEach문 사용
['e', 'f', 'g'].forEach(txt=>{
  // 1. 요소 노드 생성
  const $li = document.createElement('li');
  // 2. 텍스트 노드 생성
  const txtNode = document.createTextNode(txt);
  // 3. 텍스트 노드와 li 연결
  $li.appendChild(txtNode);
  // 4. 연결한 li를 컨테이너에 연결
  $fragment.appendChild($li);
});
// 5. 연결한 컨테이너 요소 노드를 $items에 연결
$items.appendChild($fragment);
```  
#### 4. insertBefore(newNode, childNode)  
- 지정한 위치에 노드 삽입  
- 첫 번째 인수로 전달 받은 노드를 두 번째로 전달받은 노드 <b>앞에</b> 삽입한다.  
- 두 번째 인수가 null이면 appendChild 메소드처럼 동작한다.  
```javascript  
$li.appendChild(document.createTextNode('123'));

// $li요소를 $items의 마지막 자식 요소 앞에 삽입
$items.insertBefore($li, $items.lastElementChild);
```  
#### 5. removeChild(child);  
- 인수로 전달한 노드를 DOM에서 삭제한다.  
```javascript  
// $items 요소 노드의 마지막 자식 노드 삭제
$items.removeChild($items.lastElementChild);
```  
