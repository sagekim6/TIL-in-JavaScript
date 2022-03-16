# position

문서 상의 요소 배치방법을 정의한다.

```css
element {
  position: 배치방법;
  top: 위에서 얼마나 떨어뜨릴지 정함;
  right: 오른쪽에서 얼만큼 떨어뜨릴지 정함;
  bottom: 아래에서 얼만큼 떨어뜨릴지 정함;
  left: 왼쪽에서 얼만큼 떨어뜨릴지 정함;
}
/* 상하좌우 위치 지정은 필요에 따라 선택적으로 사용! */
```

## position 속성값

#### static

기본값. 일반적인 문서의 흐름을 따른다.

#### relative

일반적인 문서 흐름(원래 자기자신의 위치)에 따라 배치하되, 상하좌우 위치 값에 따라 오프셋을 적용한다.  
위치는 이동하면서 다른 요소에는 영향을 주지 않는다.

- 오프셋: 부모요소에서 자식요소까지의 x, y거리.

#### absolute

일반적인 문서 흐름에서 제거하고, 가장 가까운 position 지정 요소(position이 적용되어 있는 요소)에 대해 상대적으로 오프셋을 적용한다. position이 지정되어 있는 요소가 없다면 뷰포트를 기준으로 잡는다.

#### fixed

일반적인 문서 흐름에서 제거하고, 지정한 위치에 고정시킨다.

#### sticky

일반적인 문서 흐름에서 제거하고, 스크롤(scroll) 되는 가장 가까운 상위 요소에 대해 오프셋을 적용한다.  
스크롤 이동으로 요소가 움직여도 sticky 요소는고정된 상태를 유지한다.

#### 연습) 이미지 2개를 position 속성을 이용해 겹쳐서 놓기  

```html
<body>
  <header>
    <h1>Title is here</h1>
    <ul>
      <li>Project</li>
      <li>Story</li>
      <li>About</li>
      <li>Contact</li>
    </ul>
  </header>
  <main class="container">
    <h2>This is heading2</h2>
    <div class="pic-wrap">
      <div class="pic1">pic1</div>
      <div class="pic2">pic2</div>
    </div>
    <p>This is description</p>
  </main>
</body>
```

```css
html,
body {
  margin: 0;
  height: 100%;
  background-color: #ffd662;
}

* {
  box-sizing: border-box;
}

ul {
  list-style: none;
  padding: 0;
}

/* Header */
header {
  background-color: #00539c;
  display: flex;
  justify-content: space-between;
  width: 100%;
  position: fixed;
  top: 0;
  z-index: 100;
}

header h1 {
  margin: 0;
  padding: 20px;
}

header ul {
  display: flex;
}

header ul li {
  padding: 10px;
}

/* Main content */
.pic1 {
  width: 1000px;
  height: 400px;
  background-color: whitesmoke;
  border: 1px black solid;
}

.pic2 {
  width: 600px;
  height: 300px;
  background-color: whitesmoke;
  border: 1px black solid;
  position: absolute;
  right: 0;
  bottom: -40px;
}

.container {
  padding: 90px 20px 50px 20px;
}

.pic-wrap {
  position: relative;
}

.container p {
  font-size: 30px;
  margin: 10px;
}
```  
<img width="960" alt="position" src="https://user-images.githubusercontent.com/94341508/158516383-ecd8171f-fc1f-450e-9548-e88e0e634785.PNG">
