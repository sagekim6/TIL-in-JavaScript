# WAI-ARIA 속성

- ARIA는 HTML 태그에 필요한 정보를 제공해 접근성 문제를 보완해주는 <u>보조 기술</u> 이다.

스크린 리더기를 사용하는 사용자들에게 페이지의 내용과 데이터가 바뀌는 영역에 역할, 속성, 상태 정보를 추가하여  
동적인 콘텐츠에 원활하게 접근하고 페이지의 접근성을 높여 사용자에게 원할한 페이지 이용을 도와준다.

- 어디까지나 보조 기술이기 때문에 HTML5에 추가된 **시맨틱 태그를 먼저 사용**하고 의미를 부가적으로 추가해야할 때 사용한다.

## `role` 속성

HTML 요소의 역할을 정의합니다.

`<element role="tablist">`

### 1. 탭 목록, 탭, 탭 패널(role="tablist|tab|tabpanel")

탭은 스타일을 의미하는 것이 아니라 현재 페이지 내용에 색인을 제공하는 구조(tablist, tab, tabpanel)를 의미한다.

`<div role="tablist"></div>`

### 2. 선택 상태(`aria-selected="true|false|undefined"`)

`aria-selected` 속성은 단일 또는 다중 선택이 가능한 요소(`role="gridcell|option|row|tab"`)에 한하여 선택 상태를 명시하는 용도로 사용합니다. `role="tab"` 요소에 가장 흔히 사용합니다. **키보드 초점을 받을 수 있는 요소(`a`, `area`, `button`, `input`, `textarea`, `object`, `select`)에 적용**해야 합니다.

- `undefined(default)`: 속성 또는 값을 선언하지 않은 경우 초기값. 선택할 수 없음.
- `true`: 선택 가능한 요소를 선택했음.
- `false`: 선택 가능한 요소를 선택하지 않았음.
