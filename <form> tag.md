# `<form>`

Client와 Server가 통신하는 방식 중 하나이다. 사용자로부터 정보를 입력 받을 수 있고 전송할 수도 있다.

1. `action` 속성: 입력받은 데이터를 전송할 url을 지정한다(장소).
2. `method` 속성: 어떤 방식으로 전송할지 지정한다(방법).

```html
<form action="URL" method="POST"></form>
```

### `<label>`

- 사용자 인터페이스를 설명할 때 사용한다.
- `for` 속성을 사용해서 `<input>` 태그와 연결하여 사용할 수 있다.  
  -> 이때 `for` 속성은 `<input>` 태그의 id값과 같아야 한다.

```html
<form>
  <label for="inputID">ID</label><br />
  <input type="text" name="inputID" id="inputID" /><br />
</form>
```

### `<input>`

1. `name`: server로 form data를 전송할 때 파라미터로 넘겨줄 이름. 중복가능하다.
2. `id`: 자바스크립트에서 `<input>`을 관리할 때 사용. 고유한 id값을 갖는다(중복불가).
3. `type`: 입력 타입을 나타낸다. 타입에 따라 여러가지 입력을 받을 수 있다.

### `<select>`

- 사용자에게 드롭다운 리스트를 제공합니다.
- 선택항목을 제공하고 선택범위 내에서 선택할 수 있다.

```html
<form>
  <label for="number">Choose a number: </label>
  <select name="number" id="number">
    <option value="one">1</option>
    <option value="two">2</option>
    <option value="three">3</option>
    <option value="four">4</option>
    <option value="five">5</option>
  </select>
</form>
```

### `<textarea>`

- 사용자에게 여러 줄의 텍스트 입력 영역을 정의할 때 사용합니다.

### `<button>`

- 사용자에게 클릭할 수 있는 버튼을 제공합니다.
- 여러 브라우저에서 기본값이 다를 수 있기 때문에 type을 button으로 명시하는 것이 좋다.

```html
<button type="button">Send</button>
```

### `<fieldset>`과 `<legend>`

- `<fieldset>`은 관련된 요소를 묶을 때 사용한다.
- `<legend>`로 캡션을 정의할 수 있다.

```html
<form>
  <fieldset>
    <legend>Login</legend>
    <label for="inputID">ID</label><br />
    <input type="text" name="inputID" id="inputID" /><br />
    <label for="inputPW">PW</label><br />
    <input type="text" name="inputPW" id="inputPW" /><br />
    <input type="submit" value="Login" /><br />
  </fieldset>
</form>
```

### `<datalist>`

- `option`목록에서 자동완성을 제공합니다.
- 범위 밖의 값도 사용자가 입력할 수 있습니다.
- `<input>`에 `list` 속성과 `<datalist>`의 id값이 같아야 합니다.

```html
<form>
  <input list="list" />
  <datalist id="list">
    <option value="1">one</option>
    <option value="2">two</option>
    <option value="3">three</option>
    <option value="4">four</option>
  </datalist>
</form>
```
