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

달러기호(`$`)를 이용해 변수를 선언한다.

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
