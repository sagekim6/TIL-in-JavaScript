# Sass(Syntactically Awesome Style Sheets)

- css를 효율적으로 작성할 수 있게 도와주는 **전처리기(Preprocessor)이다.**
- 웹은 sass가 아닌 css를 동작시킨다. 그래서 sass로 작성한 코드는 웹에서 동작 가능한 표준의 **CSS로 컴파일(Compile)해서 사용된다.**

## `React`에서 SASS 설치하기

**1. 명령어 입력**

```
npm i node-sass
```

터미널에 해당 명령어를 입력해준다. `node-sass` 라이브러리를 설치하면 sass를 css 파일로 자동으로 컴파일 해준다.  
그리고 파일 확장자를 `.css` &rarr; `.scss`로 바꾼뒤 사용하면 된다.

## 문법

### 1. 주석(Comment)

css는 주석을 `/* css 주석 */` 이렇게 다는데 sass도 css주석을 따라서 달지만 JavaScript 주서도 같이 사용한다.

`/* css 주석 -> 컴파일되는 주석 */`  
`// JavaScript 주석 -> 컴파일되지 않는 주석`

### 2. 데이터 타입

sass에는 데이터 타입이 존재한다.

|  데이터  |                                                                | 예제                                             |
| :------: | :------------------------------------------------------------: | :----------------------------------------------- |
| Numbers  |                              숫자                              | `1`, `.82`, `20px`, `2em`                        |
| Strings  |                              문자                              | `bold`, `relative`, `"/images/a.png"`, `"dotum"` |
|  Colors  |                           색상 표현                            | `red`, `blue`, `#FFFF00`, `rgba(255,0,0,.5)`     |
| Booleans |                              논리                              | `true`, `false`                                  |
|  Nulls   |   아무것도 없음. 속성값으로 null이 사용되면 컴파일하지 않음    | `null`                                           |
|  Lists   |                 공백이나 ,로 구분된 값의 목록                  | `(apple, orange, banana)`, `apple orange`        |
|   Maps   | Lists와 유사하나 값이 `Key: Value` 형태. `()`를 반드시 붙인다. | `(apple: a, orange: o, banana: b)`               |

### 3. 변수 선언

- 달러기호(`$`)를 이용해 변수를 선언한다.
- `{}` 중괄호 안에서만 유효하며 재할당이 가능하다.
- `!global` 플래그를 사용하면 변수의 유효범위를 전역(Global)로 설정할 수 있다.
- `#{}` 문자 보간을 이용해 코드 중간에 변수를 넣을 수 있다.

```css
$변수명: 값;
```

```css
// 변수 언언
$red: red;

.title {
  color: $red; // 변수명으로 사용
}
```

### 4. 중첩(Nesting)

상위 선택자의 중복을 피하면서 선택자를 선택할 수 있다.

```css
$red: red;
$green: green;

.title {
  color: $green;
  .Sass {
    $red: red;
  }
}
```

#### `@at-root` 중첩 벗어나기

중첩에서 벗어나고 싶을 때 `@at-root` 키워드를 사용한다. 중첩 안에서 생성하되 중첩 밖에서 사용해야 경우에 유용합니다.

```css
.list {
  $w: 100px;
  $h: 50px;
  li {
    width: $w;
    height: $h;
  }
  @at-root .box {
    // 중첩문 안에 선언한 변수를 사용할 때
    width: $w;
    height: $h;
  }
}
```

해당 scss문은 아래 css로 컴파일된다.

```css
.list li {
  width: 100px;
  height: 50px;
}
.box {
  width: 100px;
  height: 50px;
}
```

### 5. `@mixin` 재활용

재사용 할 css 선언 그룹을 지정해 사용할 수 있다.  
`@mixin` 키워드로 선언한뒤 `@include` 키워드로 사용합니다.

```css
// 믹스인 선언
@mixin 믹스인이름 {
  스타일;
}

// 믹스인 사용
@include 믹스인이름;
```

```css
@mixin pink-border {
  border: 1px solid pink;
  padding: 1rem;
}

p {
  @include pink-border();
}
```

#### 인수(Arguments) 받기

믹스인은 함수처럼 인수를 받아서 사용할 수 있다.

```css
@mixin border($color) {
  border: 1px solid $color;
  padding: 1rem;
}

p {
  @include border(green);
}
```

#### 인수의 기본값 설정

인수가 전달되지 않았을 때 기본값으로 적용된다.

```css
@mixin 믹스인이름($매개변수: 기본값) {
  스타일;
}
```

```css
// black으로 적용된다
@mixin border($color: black) {
  border: 1px solid $color;
  padding: 1rem;
}

p {
  @include border(); // 인수가 전달되지 않음
}
```
