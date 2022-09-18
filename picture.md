# `<picture>` 태그

- `<picture>` 태그를 사용하면 디스플레이에 따라 보다 **유연하게 이미지를 노출**할 수 있습니다.

```html
<picture>
  <source srcset="/images/wide_image.jpg" media="all and (min-width: 800px)" />
  <img src="/images/default.jpg" alt="default" />
</picture>
```

- source 요소 중에서 srcset, media, type 와 같이 **선언된 속성(Attributes) 들을 통해 기기에 적합한 이미지를 노출**하게 됩니다.
  - 브라우저가 적합한 이미지를 찾았다면 다음 source 요소는 무시하기 때문에 **source 요소를 선언할 때는 순서에 유의하며 코드를 작성**해야 합니다.
- 적합한 요소가 선언되어 있지 않거나 브라우저가 **picture를 지원하지 않을 때에는 IMG에서 선언된 이미지가 노출**됩니다.

&rarr; 즉, `source` 속성이 제공하는 정보에 따라 적합한 이미지가 노출되고 그렇지 못한 경우에는 `img` 태그가 대체 이미지를 제공한다.
