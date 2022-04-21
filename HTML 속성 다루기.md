# HTML 속성 다루기

- 표준 속성이 아닌 경우 프로퍼티로 변환이 안 되지만 아래 메소드를 활용하면 표준이 아닌 HTML 속성들도 다룰 수 있다.

```html
<!-- 연습 코드 -->
<body>
  <a href="https://www.naver.com/" id="link">Go to naver</a>
</body>
```

### elem.getAttribute('속성') : 요소 노드의 속성에 접근하기

```javascript
const link = document.querySelector("#link");
const getAtt = link.getAttribute("href");
console.log(getAtt);
```

### elem.setAttribute('속성', '값') : 요소 노드의 속성 추가(수정)하기

```javascript
link.setAttribute("target", "_blank");
```

### elem.removeAttribute('속성') : 요소 노드의 속성 제거하기

```javascript
link.removeAttribute("target");
```
