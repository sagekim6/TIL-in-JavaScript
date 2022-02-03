# 웹 접근성

- 웹 사이트에서 제공하는 정보를 신체적인 조건이나 환경적인 조건에 관계없이 동등하게 접근하고 이용할 수 있도록 보장하는 것을 의미   
-> 다양한 디바이스와 플랫폼을 지원하고 장애가 있거나 고령자인 경우에도 웹 사이트를 이해할 수 있게 하는 것

# 웹 표준

- 웹에서 표준으로 사용 되는 기술이나 규칙  
  구초(Markup)-HTML, 표현(Style)-css, 동작(Script)-Javascript으로 나누어 개발한다

# 웹 표준 항목

1.논리적이고 의미에 맞는 마크업  
2.최신 버전의 브라우저에 호환  
-> 웹 표준을 준수하면 다양한 플랫폼과 디바이스에 호환이 가능하고 웹 접근성이 향상되는 효과를 얻을 수 있다.

# 검색엔진 최적화(SEO)

- 검색 엔진이란 구글, 네이버, 다음 등에서 제공하는 검색 프로그램으로 공개되어있는 웹 문서를 검색하기위해 사용된다.  
- 봇이 수집하고 분류해 놓은 수많은 검색 결과 중에 내 웹 사이트가 앞쪽에 상위에 노출되게 해야한다.  
- 봇은 html문서를 수집한다->html문서를 봇이 잘 해석할 수 있게끔 분명하게 작성하는 것이 중요하다.

  - 웹 접근성, 웹 표준을 준수하여 마크업을 한다
  - `<head>`안에 제공하는 `<meta></meta>`태그를 정확하고 간결하게 작성한다.
  - html 시맨틱 태그를 잘 사용한다.

- 메타 태그`<meta></meta>`
  - 크롤러가 만들어 놓은 웹 사이트를 잘 크롤링해 색인에 저장할 수 있게 마크업을 한다.
  - `<title></title>` : 최대 40글자 내로 작성-> 검색했을 때 요약된 정보를 받아볼 수 있다
  - `<meta name="description" content="HTML meta and tag page">` : 웹 페이지에 대한 설명을 정의한다(160자 이내를 권장)  
    -> 검색엔진에 영향은 없지만 CTR(클릭율)에 영향을 미치기 때문에 잘 작성해 주는 것이 좋다.
  - `<meta name="keyword" content="HTML, meta, tag, element, reference">` : 검색엔진을 위한 키워드를 정의한다
  - `<meta name="robots" content="index,follow">` : 크롤링 봇 및 색인 허용  
    -> index는 색인을 follow는 링크를 따라서 크롤러가 이동할 것인지 아닌지를 나타낸다.  
    -> 허용하지 않으려면`content="noindex, nofollow"` content부분에 no를 붙여준다.
  - 소셜 미디어 Open graph 정보 : sns에 특정 사이트의 게시물을 공유할 때  
    og(오픈 그래프)에 지정해 놓은 사이트 정보를 크롤링해서 뿌려줄 때 사용
    - `<meta property="og:type" content="website">`
    - `<meta property="og:title" content="페이지 제목">`
    - `<meta property="og:description" content="페이지 설명">`
    - `<meta property="og:image" content="페이지 썸네일 이미지 주소">`->url작성, 이미지 해상도는 1200X630권장
    - `<meta property="og:url" content="페이지 주소">`

## 구글 크롤러

### 1. 색인(index)

- 구글에서는 모든 웹 페이지를 색인에 저장한다.

### 2. crawling

- 특정 웹 사이트에서 데이터를 추출해내는 행위  
  -> 추출된 데이터는 색인에 저장된다

### 3. Web crawler

- crawling을 하는 소프트웨어. crawling하고 색인에 저장시키는 자동 소프트웨어다.
  - 구글에서 사용하는 크롤러를 Google bot(구글봇)이라고 한다.
