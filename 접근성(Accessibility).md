# 접근성(Accessibility)

### `img` 태그에 `alt` 속성은 필수

- alt 속성은 이미지를 로드하는데 실패 했을 때 해당 이미지를 대체할 텍스트를 설정한다.
- alt 속성을 사용하면 이미지 정보가 노출되기 때문에 검색 엔진이 페이지에 대한 주제를 잘 해석할 수 있게 한다.
- 해당 이미지의 간단한 설명을 넣어주는 것이 좋다.
- 만약 이미지가 아무 의미가 없다면(단순 장식) alt속성을 공백으로 남겨도 된다.
- a 태그 안에 이미지가 있다면 링크가 어디로 연결되는지 묘사해야한다.

```html
<a href="https://www.naver.com/" alt="go to naver"></a>
```

### heading 태그를 사용해 중요도 표현하기

- 스크린리더는 heading 태그만 읽어서 사용자에게 간단한 요약 정보를 주기도 한다.
- h1 태그는 한 페이지당 하나만 사용하는 것이 좋다.

### `figure`, `figcaption` 태그 사용

- 연관된 컨텐츠를 묶어 접근성을 높인다.
- figure 태그는 그림, 도표, 그래프 등과 같은 문서의 흐름과는 독립적인 콘텐츠를 표현하는 데 사용한다.  
  -> img 태그와 비슷해 보이지만 figure 태그는 src, alt속성을 사용할 수 없다.
- figcaption 태그로 figure 태그에 설명을 달아준다.(옵션)  
  -> figure 태그의 첫 번째 혹은 마지막에 위치한다.

```html
<figure>
  <img src="newsImage.png" alt="newsImage" />
  <!-- figure태그의 설명으로 마지막에 위치 -->
  <figcaption>땡땡 뉴스 사진1-여름 피서지 풍경</figcaption>
</figure>
```

### `time` 태그와 `datetime` 속성

- 인라인 요소로 페이지 내에서 시간이나 날짜를 묶어줄 때 사용한다.
- 일반 텍스트로 보이는 부분이 실제 날짜 정보라는 것을 html에 알려주기 위해 사용.
- `datetime`속성을 이용해 기계가 읽을 수 있는 날짜와 시간을 명시한다.

```html
<!-- 단순 텍스트 어떤 정보도 표현하지 않는다. -->
<p>1997-02-13</p>
```

```html
<!-- 단순 텍스트가 아니라 실제 날짜 정보임을 html에 알려준다.  -->
<time datetime="1997-02-13">
  <p>1997-02-13</p>
</time>
```

### `tabindex` 속성

- tab 키의 포커스를 순서를 조정하는 속성
- 마우스 사용이 안 될 때 키보드 만으로도 조작이 가능하게 한다.
- tabindex를 양수로 중구난방 지정하게 되면 혼란스러울 수 있으니 주의 해야한다.

```html
<!-- div 태그 처럼 상호작용 하지 않는 태그에는 속성값을 0으로 해준다. -->
<div tabindex="0">연락처</div>
```

```html
<!-- 해당 요소에 포커스가 잡히지 않게 하려면 속성값을 -1로 설정한다. -->
<h3 tabindex="-1">제목 3번</h3>
```

```html
<form>
  <label>
    <span>이름: </span>
    <!-- 속성값을 양수로 지정하면 오름차순으로 포커스 순서를 지정할 수 있다. -->
    <input type="text" name="name" tabindex="1" />
  </label>
  <label>
    <span>이메일: </span>
    <input type="email" name="email" tabindex="2" />
  </label>
</form>
```
