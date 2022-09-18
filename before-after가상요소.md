# `::before`, `::after` 가상요소

- 해당 태그 앞, 뒤로 콘텐츠를 추가하고 싶을 때 사용한다.
- 인라인 요소이다.
- `content` 속성을 사용해 콘텐츠를 주가할 수 있다.
  - `content` 속성을 추가해야 가상요소가 만들어지므로 필수 속성이다.

## `::before`

```css
p::before {
  content: "●";
  color: green;
}
```

`<p>` 태그의 **앞쪽**에 content로 지정해준 초록색 '●'가 추가됩니다.

## `::after`

```css
p::after {
  content: "●";
  color: green;
}
```

`<p>` 태그의 **뒤쪽**에 content로 지정해준 초록색 '●'가 추가됩니다.
