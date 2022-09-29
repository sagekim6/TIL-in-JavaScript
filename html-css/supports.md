# `@supports`

- CSS 기능을 **웹브라우저가 지원하는 지에 따른 스타일 선언**을 할 수 있도록 해준다.

### 기본 문법

```css
@supports ( 속성: 값 ) {
  선언
}

@supports not (속성: 값) {
  선언
}
```

조건 안에 넣어준 속성과 속성값이 해당 브라우저에서 지원되는 기능이라면 선언된 css 스타일이 적용된다.  
`not` 연산자를 사용하면 해당 조건에 해당하는 속성을 지원하지 않을 때 선언된 스타일이 적용된다.

```css
.primary-navigation {
  list-style: none;
  margin: 0;
  padding: 0;
  --underline-gap: 2rem;
  background-color: rgb(var(--clr-black-color), 90%);
}

@supports (backdrop-filter: blur(1rem)) {
  .primary-navigation {
    background-color: rgb(var(--clr-white-color), 7%);
    backdrop-filter: blur(1.5rem);
  }
}
```

`backdrop-filter` 속성을 지원하지 않는 브라우저도 있기 때문에 해당 기능을 지원하는 브라우저에서는 `backdrop-filter: blur(1.5rem)`을 적용하고  
지원하지 않는 다면 `.primary-navigation` 클래스에서 선언된 스타일이 적용된다.
