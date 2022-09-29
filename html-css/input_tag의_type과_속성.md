# HTML `<input>` types

### default `text`

`<input>` 태그의 기본값이며 한 줄짜리 텍스트 입력필드를 제공한다.

```html
<form>
  <label>First name:</label><br />
  <input type="text" /><br />
  <label>Second name:</label><br />
  <input type="text" />
</form>
```

### `password`

비밀번호 입력필드를 제공한다. 입력된 문자는 별표(\*) 혹은 점으로 표시된다.

```html
<form>
  <label for="passwordLogin">Password</label><br />
  <input type="password" id="passwordLogin" name="password" required /><br />
</form>
```

### `submit`

`<form>`태그의 `action` 속성에 지정해준 URL로 데이터를 전송해줄 수 있는 버튼을 제공한다.

```html
<input type="submit" />
```

기본값으로 '제출' 혹은 'submit'이라고 적힌 버튼이 제공되고 `value` 속성을 통해 기본값을 변경가능하다.

### `reset`

폼안에 입력된 데이터를 초기화 시키는 버튼을 제공한다.

```html
<form>
  <label>주소</label><br />
  <input type="address" name="address" id="address" /><br />
  <label>받는이</label><br />
  <input type="text" /><br />
  <label>전화번호</label><br />
  <input type="tel" placeholder="000-0000-0000" /><br />
  <!-- 주소, 이름, 번호를 초기화 시킨다 -->
  <input type="reset" />
</form>
```

### `color`

색을 선택할 수 있는 입력필드(color picker)를 제공한다.

```html
<form>
  <label>배경색을 선택하세요:</label><br />
  <input type="color" />
</form>
```

### `file`

사용자의 로컬파일을 입력받을 수 있는 입력필드를 제공한다.

```html
<!-- multiple 속성을 추가 하면 여러개의 파일을 선택할 수 있다. -->
<input type="file" multiple />
```

### `hidden`

사용자에게 보이지 않는 숨겨진 입력 필드를 제공한다. 하지만 개발자도구를 열어보면 소스를 볼 수 있음으로 보안용으로 사용해서는 안 된다.  
사용자가 변경해선 안 되는 입력이 있을 때 사용된다.

```html
<input type="hidden" />
```

### `search`

언뜻 보면 `text` 속성과 같아 보이지만 텍스트를 입력하면 오른쪽에 입력한 값을 전체삭제할 수 있는 X표시가 나타납니다.

```html
<input type="search" />
```

## Attributes

### 1. `value` 속성

`<input>`의 초기값을 설정한다.

### 2. `readonly` 속성

`<input>`을 읽기전용으로 설정한다. 변경만 불가능하고 탭이나 복사는 가능하다.

### 3. `disabled` 속성

`readonly` 속성과 비슷하게 변경할 수 없지만 탭과 복사는 가능하다. 하지만 데이터는 전송되지 않는다.

### 4. `size` 속성

`<input>`의 타입이 `text`일 경우 입력필드의 넓이를 정의하고 `<select>` 태그에서는 높이를 정의한다.

### 5. `step` 속성

`<input type="number, range, date, datetime-local, month, time, week>`인 경우 숫자의 이동간격을 지정하는 속성.

```html
<!-- 최소1, 최대10인 범위를 1.0씩 이동 -->
<form>
  <input type="range" min="1" max="10" step="1.0" />
</form>
```

### 6. `autofocus` 속성

`<input>` 태그에 자동으로 포커스를 가지게 한다.

```html
<form>
  <input type="text" autofocus />
</form>
```

### 7. `autocomplete` 속성

자동완성 기능을 제공한다. 과거에 입력된 값들 중 유사한 값들을 제공한다.

```html
<!-- on/off로 속성을 켜고 끌 수 있다 -->
<form>
  <input type="text" autocomplete="on" />
</form>
```
