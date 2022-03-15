# float and clear

## float 속성

요소가 문서의 일반적인 흐름에서 제외되어 자신을 포함하고 있는 컨텡너의 왼쪽이나 오른쪽에 배치되게 한다.

1. none: 기본값, 원래 상태
2. left: 자신을 포함하고 있는 박스의 왼편에 떠있는 상태
3. right: 자신을 포함하고 있는 박스의 오른편에 떠있는 상태

-> 문서의 흐름에선 제외되지만, 필요한 만큼의 공간은 차지한다.

## clear 속성

float 속성을 사용했을 때 문서의 흐름에서 제외시켜 레이아웃을 잡을 수 있다는 장점이 있지만  
float 요소 다음에 오는 요소가 자리를 못잡고 헤매게되는 경우가 있다.  
이때 clear 속성을 사용하면 float 요소 이후에 표시되는 요소가 float을 해제하여 float 요서의 아래로 내려가게 할 수 있다.

1. none: 기본값
2. left: float이 left인 요소의 아래로 내려감
3. right: float이 right인 요소의 아래로 내려감
4. both: float이 left와 right인 요소의 아래로 내려감

-> both 속성값으로 간단하게 해결가능하다.

#### 예습)

```html
<body>
  <div class="wrapper">
    <div class="item-list">
      <h1>연관 영상</h1>
      <div class="item">
        <div class="video">영상</div>
        <h2>비디오1</h2>
        <p>조회수 2.8천회</p>
        <div class="clear"></div>
      </div>
      <div class="item">
        <div class="video">영상</div>
        <h2>비디오2</h2>
        <p>조회수 2.8천회</p>
        <div class="clear"></div>
      </div>
      <div class="item">
        <div class="video">영상</div>
        <h2>비디오3</h2>
        <p>조회수 2.8천회</p>
        <div class="clear"></div>
      </div>
      <div class="item">
        <div class="video">영상</div>
        <h2>비디오4</h2>
        <p>조회수 2.8천회</p>
        <div class="clear"></div>
      </div>
      <div class="item">
        <div class="video">영상</div>
        <h2>비디오5</h2>
        <p>조회수 2.8천회</p>
        <!-- clear 속성을 적용해줄 요소를 만든다. -->
        <div class="clear"></div>
      </div>
    </div>
  </div>
</body>
```

```css
/* 다른 스타일도 적용되었지만 float속성과 clear 속성만 가져옴 */
.video {
  width: 130px;
  height: 90px;
  background-color: darkgray;
  float: left;
  border-radius: 4px;
  margin-right: 8px;
}

.clear {
  clear: both;
}
```  
<img width="335" alt="float" src="https://user-images.githubusercontent.com/94341508/158305996-a7c98e27-e5e6-4f60-a96a-79e7ea8f9ec0.PNG">
