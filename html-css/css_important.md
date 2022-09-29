# !important

- CSS에는 선택자에 따른 우선순위도 있지만 `!important`를 사용해서 우선순위를 주는 방법도 있다.
- 요소에 정확한 CSS 스타일링을 주고 싶을 때 사용해주는게 좋다.
- `!important` 키워드가 붙은 요소에는 다른 css속성이 붙어도 전부 무시된다.

```html
<style>
  /* id선택자를 이용해 css속성을 줬기 때문에 폰트색상이 red로 설정될것 같지만 */
  #heading1 {
    color: red;
  }

  /* !important 속성을 사용하면 해당 속성이 변경되지 않도록 하는 역할을 하기 때문에
     red가 아닌 pink로 설정된다.
  */
  h1 {
    color: pink !important;
  }
</style>
<body>
  <h1 id="heading1">important</h1>
</body>
```
