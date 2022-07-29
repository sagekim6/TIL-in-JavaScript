# CSS선택자

```javascript
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
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laudantium,
        maxime adipisci saepe sequi aliquam dolorum laborum, nemo expedita
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

#### 특성 선택자 : 주어진 특성의 존재 여부나 그 값에 따라 요소를 선택

```javascript
    <style>
    // a태그의 href="#"인 태그를 선택해 글자색을 검은색으로 변경
      a[href="#"] {
        color: black;
      }
    </style>
```

#### 후손 선택자 : 부모요소의 후손 요소를 모두 선택

```javascript
    <style>
    // container 클래스의 후손 요소를 전부 선택하여 배경색을 초록색으로 변경
      .container li {
        background-color: green;
      }
    </style>
```

#### 자식 선택자(>) : 부모요소의 자식 요소를 모두 선택

```javascript
    <style>
    // container 클래스 요소의 자식 요소인 p태그 선택
      .container > p {
        background-color: green;
      }
    </style>
```

#### 인접 형제 선택자(+) : 같은 계층에 있을 때 요소 바로 뒤에 있는 요소를 선택

```javascript
    <style>
    // #heading과 p가 같은 계층에 있을 때 사용. #heading바로 뒤에 있는 p태그 선택
      #heading + p {
        background-color: pink;
      }
    </style>
```

#### 일반 형제 선택자(~) : 같은 계층에 있을 때 요소 바로 뒤에 위치하는 모든 요소 선택

```javascript
    <style>
    // #heading과 같은 계층의 모든 p태그 선택
      #heading ~ p {
        color: pink;
      }
    </style>
```
