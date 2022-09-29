# Client-Side Form Validation

서버로 폼 데이터를 전송하기 전에 제대로된 데이터가 입력됬는지 client 쪽에서 1차로 확인하는 작업이다.  
1차로 client 쪽에서 검증하는 작업을 거치지만 그게 끝이 아니라 server 쪽에서 2차로 검증하는 과정을 거치는게 좋다.

데이터를 전송하기 전 검증과정을 거쳐야 하는 이유는:

1. 올바른 데이터가 입력되어야 제대로된 서비스를 제공할 수 있다.
2. 사용자의 정보를 보호할 수 있다.
3. 악의적인 데이터가 입력되는 것을 방지할 수 있다.

### Using Built-in Form validation

가장 쉽고 기본적인 방법으로 이미 있는 속성을 사용하는 것이다.

1. `required`: 필수로 입력하게 하는 속성
2. `min` `max`: 최소, 최대 정수를 지정해 제한을 둔다.
3. `minlength` `maxlength`: 최대, 최소 글자수를 지정해 제한을 둔다.
4. `type`: email, password, number 등 여러 타입을 지정할 수 있다.
5. `pattern`: 정규표현식을 이용해 입력되는 데이터를 구체화할 수 있다.

`min` `max`를 사용해 음수값은 나이로 설정할 수 없게 설정  
`pattern` 속성으로 `<input>` 값을 구체적으로 입력하게 함.

```html
<form>
  <label for="choose">Would you prefer banana or cherry?</label>
  <input
    type="text"
    id="choose"
    name="i-like"
    required
    pattern="[Bb]anana|[Cc]herry"
  />
  <label for="age">How old are you?</label>
  <input type="number" name="years-old" id="age" min="1" max="100" />
  <button type="button">submit</button>
</form>
```

### CSS pseudo-class

CSS 가상 클래스를 사용해 요소의 스타일을 지정해 시각적으로도 보여줄 수 있다.

`:valid`: 규칙에 맞는 입력일 경우  
`:invalid`: 규칙에 맞지 않는 입력일 경우

```html
<style>
  input:valid {
    border: 2px green solid;
  }
  input:invalid {
    border: 2px red solid;
  }
  input:invalid:required {
    background-image: linear-gradient(to right, pink, lightgreen);
  }
</style>
```

실습으로 만들어본 로그인폼

```html
<body>
  <form action="#">
    <fieldset>
      <h2>Welcom!</h2>
      <label for="emailLogin">Email</label><br />
      <input type="email" id="emailLogin" name="email" required /><br />
      <label for="passwordLogin">Password</label><br />
      <input
        type="password"
        id="passwordLogin"
        name="password"
        required
      /><br />
      <input type="submit" value="Login" class="submit-btn" /><br />
      <div class="links">
        <a href="#" class="forgetPWlink">Forgot password?</a>
        <a href="#" class="signUpLink">Sign up</a>
      </div>
    </fieldset>
  </form>
</body>
```

<img width="662" alt="로그인폼" src="https://user-images.githubusercontent.com/94341508/158065677-e06e95a5-e14d-414c-9f1c-e1b885c3d1e3.PNG">
