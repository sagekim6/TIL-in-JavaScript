# Grid

grid 속성은 행과 열이 있는 그리드 기반의 레이아웃을 제공합니다. 부모 요소가 하나 있고 자식요소를 하나 이상 가집니다.  
grid를 사용하려면 flex-box를 사용하듯이 부모요소에 display:grid;를 선언해줍니다.

```css
.container {
  display: gride;
}
```

선언하게 되면 자식 요소는 자동적으로 grid-item이 됩니다. 그리고 block요소가 되어 한 줄의 column이 됩니다.  
그리고 이 column과 row를 track이라고 부릅니다.

## grid-template-columns/rows

그리드 track의 크기를 지정해주는 속성. 여러 단위를 섞어서 사용할 수 있다.

### `grid-template-columns`

column의 수와 width를 지정하는 속성.  
만약 column 3개를 지정하고 싶다면...!

```css
.container {
  display: grid;
  /* 넓이가 100px인 column 3개를 만들 수 있다. */
  grid-template-columns: 100px 100px 100px;
}
/* 만약 부모 요소에 아이템이 4개가 있다면 자동적으로 다음줄로 넘어간다. */
```

```css
.container {
  display: grid;
  /* 부모요소의 넓이에 맞춰 아이템 3개가 같은 넓이를 갖는다. */
  grid-template-columns: auto auto auto;
}
```

### `grid-template-rows`

row 각각의 height을 지정하는 속성

```css
.container {
  display: grid;
  /* 첫 번째 row의 높이는 100px이 되고 두 번째 row의 높이는 50px이 된다. */
  grid-template-rows: 100px 50px;
}
```

<strong>repeat()함수를 사용해 많은 column과 row를 정의할 수 있다.</strong>

- repeat(반복 횟수, 크기)

```css
.container {
  display: grid;
  /* 넓이가 50px인 column을 10개 만든다는 의미 */
  grid-template-columns: repeat(10, 50px);
}
```

### `grid-auto-columns/rows`

column이나 row가 얼마나 들어갈지 확실하지 않다면 `grid-auto` 속성을 통해 자동으로 횟수를 지정되게 할 수 있다.

```css
.container {
  border: 2px black solid;
  display: grid;
  /* 최소 넓이가 150px이고 최대는 자동으로 늘어납니다. 반복 횟수는 부모 요소에 따라 달라지고
     최소 넓이가 150px이기 때문에 150px 이하가 되면 아이템이 다음줄로 넘어갑니다.
  */
  grid-template-columns: repeat(auto-fill, minmax(150px, auto));
  /* 최소 높이가 200px이고 최대 높이는 자동으로 늘어납니다.
     또한 grid-auto이기 때문에 반복 횟수도 자동으로 늘어납니다.
     -> column에서 넘어오는 아이템이 있다면 자동으로 row의 갯수가 늘어납니다.
  */
  grid-auto-rows: minmax(200px, auto);
  gap: 10px;
}
```

## `gap`

행과 열 사이의 간격을 주는 속성
| 속성 | 기능 |  
|:-----|:-----|  
|column-gap|세로 사이 간격|  
|row-gap|가로 사이 간격|  
|gap|가로와 세로 사이 간격|

```css
.container {
  display: grid;
  gap: 50px 10px;
  /* gap: row(가로) column(세로); 단축 속성 */
}
```

## `minmax()`

column과 row의 최소, 최대 크기를 지정합니다.  
row 높이보다 큰 그리드 아이템이 들어올 때 최소, 최대 높이를 정해주지 않으면 overflow가 발생합니다.  
최대 높이를 auto로 지정하면 그리드 아이템에 따라 높이가 늘어납니다.

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  /* row의 최소 높이 50px, 최대 높이 auto로 지정 */
  grid-auto-rows: minmax(50px, auto);
  gap: 10px;
}
```

## `auto-fill`

column, row의 개수를 부모 요소의 크기에 맞게 자동으로 조절해 줍니다. 보다 쉽게 반응형을 만들 수 있다.

```css
.container {
  display: grid;
  /* column의 개수는 auto-fill, 최소 넓이는 150px, 최대 넓이는 자동으로 지정 */
  grid-template-columns: repeat(auto-fill, minmax(150px, auto));
  /* 최소 높이 150px, 최대 높이는 자동으로 지정 */
  grid-auto-rows: minmax(150px, auto);
  gap: 10px;
}
```

## Grid Lines

column 사이에 있는 라인을 column-line이라 하고 row 사이에 있는 라인을 row-line이라고 합니다.  
그리드 라인을 이용해 아이템의 영역을 지정할 수 있습니다.

![GrideLines](https://www.w3schools.com/css/grid_lines.png)

### `grid-column-start/grid-column-end/grid-column`

### `grid-rows-start/grid-rows-end/grid-rows`

line의 시작점과 끝점을 지정햐주는 속성
| 속성 | 기능 |  
|:-----|:-----|  
|grid-column-start/grid-rows-start|line의 시작점 지정|  
|grid-column-end/grid-rows-end|line의 끝점 지정|  
|grid-column/grid-rows| line의 끝점, 시작점을 한 줄에 지정|

```html
<body>
  <div class="container">
    <header>
      <h1>Logo is here.</h1>
      <nav>
        <ul>
          <li>list1</li>
          <li>list2</li>
          <li>list3</li>
          <li>list4</li>
        </ul>
      </nav>
    </header>
    <main>main content will be here.</main>
    <aside>aside</aside>
    <footer>footer</footer>
  </div>
</body>
```

```css
html,
body {
  height: 100%;
}

.container {
  height: 100%;
  display: grid;
  grid-template-columns: 4fr 1fr;
  grid-template-rows: 10% 80% 10%;
}

header {
  background-color: yellowgreen;
  /* column-line을 1부터 3까지 전부 차지하게 header영역 지정 */
  grid-column: 1/3;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header ul {
  display: flex;
}

header ul li {
  padding: 15px;
}

main{
  background-color: tomato;
}

aside {
  background-color: cornflowerblue;
}

footer {
  background-color: indianred;
  /* column-line을 1부터 3까지 전부 차지하게 footer영역 지정 */
  grid-column: 1/3;
}
```  
<img width="960" alt="gride-line-layout" src="https://user-images.githubusercontent.com/94341508/158753185-2d7d48a6-0b19-48cd-bb4b-62eca52af15d.PNG">  
  
## grid-template-area

각 그리드 영역에 이름을 붙이고 이름을 이용해 아이템을 배치하는 것.

```html
<body>
  <div class="container">
    <header>
      <h1>Logo is here.</h1>
      <nav>
        <ul>
          <li>list1</li>
          <li>list2</li>
          <li>list3</li>
          <li>list4</li>
        </ul>
      </nav>
    </header>
    <div class="a">a</div>
    <main>main content will be here.</main>
    <div class="b">b</div>
    <footer>footer</footer>
  </div>
</body>
```

```css
html,
body {
  height: 100%;
}

.container {
  height: 100%;
  display: grid;
  /* 쌍따옴표 안에 이름을 써준다 */
  grid-template-areas:
    /* header가 될 부분이 column 3개를 차지하게 만들고 싶으면
      이름을 3번 써주면 된다
    */
    "header header header"
    "a main b"
    "footer footer footer";
  /* column이 3개 row가 3개인 그리드 완성 */
  grid-template-rows: 10% 80% 10%;
  grid-template-columns: 10% 80% 10%;
}

header {
  background-color: yellowgreen;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* grid-area속성을 사용해 아이템에 이름을 붙여준다 */
  grid-area: header;
}

header ul {
  display: flex;
}

header ul li {
  padding: 15px;
}

main {
  background-color: tomato;
  grid-area: main;
}

aside {
  background-color: cornflowerblue;
}

footer {
  background-color: indianred;
  grid-area: footer;
}

.a {
  background-color: darkgreen;
  grid-area: a;
}

.b {
  background-color: rebeccapurple;
  grid-area: b;
}
```  

<img width="960" alt="grid-template-area" src="https://user-images.githubusercontent.com/94341508/158782372-c773f3c2-9a8a-4134-ac0f-37675807d06a.PNG">
