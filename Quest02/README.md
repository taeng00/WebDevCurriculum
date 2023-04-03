# Quest 02. CSS의 기초와 응용

## Introduction

- CSS는 Cascading StyleSheet의 약자입니다. 웹브라우저에 표시되는 HTML 문서의 스타일을 지정하는 (거의) 유일하지만 다루기 쉽지 않은 언어입니다. 이번 퀘스트를 통해 CSS의 기초적인 레이아웃 작성법을 알아볼 예정입니다.

## Topics

- CSS의 기초 문법과 적용 방법
  - Inline, `<style>`, `<link rel="stylesheet" href="...">`
- CSS 규칙의 우선순위
- 박스 모델과 레이아웃 요소
  - 박스 모델: `width`, `height`, `margin`, `padding`, `border`, `box-sizing`
  - `position`, `left`, `top`, `display`
  - CSS Flexbox와 Grid
- CSS 표준의 역사
- 브라우저별 Developer tools

## Resources

- [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)
- [A complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [그리드 레이아웃과 다른 레이아웃 방법과의 관계](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout/%EA%B7%B8%EB%A6%AC%EB%93%9C_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EB%8B%A4%EB%A5%B8_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83_%EB%B0%A9%EB%B2%95%EA%B3%BC%EC%9D%98_%EA%B4%80%EA%B3%84)

## Checklist

- CSS를 HTML에 적용하는 세 가지 방법은 무엇일까요?

  1. Inline Style Sheet : HTML 태그의 style 속성에 CSS 코드를 넣는 방법

     > HTML 태그에 직접 작성하기 때문에 특정 영역에 스타일을 적용하고 싶을 때 가장 빠른 방법이지만, HTML 파일의 사이즈를 너무 크게 만들어서, 화면에 웹페이지가 로딩되는 시간을 오래 걸리게 함. 또한, HTML과 CSS가 코드에 뒤섞이게 되어 유지보수를 어렵게 하기도 함.

  2. Internal Style Sheet : HTML 문서 안의 <style>과 </style> 안에 CSS 코드를 넣는 방법

     > Inline 처럼 css가 HTML 파일 내부에 정의 됨. 둘의 차이는 Inline은 특정 HTML 태그에만 style이 적용되지만, Internal은 <head> 태그가 로드되는 하위의 모든 HTML 페이지에 스타일이 적용.

  3. External(Linking) Style Sheet : 별도의 CSS 파일을 만들고 HTML 문서와 연결하는 방법

     > CSS와 HTML이 물리적 파일로 분리, 유지보수가 편해 일반적으로 가장 많이 사용.

- CSS 규칙의 우선순위는 어떻게 결정될까요?

  1. 적용 방법에 따른 우선 순위
     > Inline > Internal > External > 웹 브라우저 기본 스타일
  2. 적용 범위에 따른 우선 순위
     > !important : 어떤 스타일보다 가장 우선으로 적용되는 스타일 > Inline 스타일 : 태그안에 style 속성을 사용하여 스타일 적용 > id 스타일 : 하나의 요소에 스타일 적용(선택자 앞에 # 기호 사용) > class 스타일 : 여러 요소 들에 스타일 적용(선택자 앞에 . 기호 사용) > type(tag) 스타일 : 특정 태그를 사용 하는 모든 요소에 스타일 적용

- CSS의 박스모델은 무엇일까요? 박스가 화면에서 차지하는 크기는 어떻게 결정될까요?

  > 모든 HTML 요소는 사각형 박스 모양으로 구성되며, 이것이 박스 모델(box model). CSS는 박스의 크기, 위치, 속성(색, 배경, 테두리 모양 등)을 결정.

  <p align="center">
    <img src="https://user-images.githubusercontent.com/124439821/229369611-47846d0c-0a52-448d-864f-3f4105e5af32.png">
  </p>

       1. content : 텍스트나 이미지가 들어있는 박스의 실질적인 내용.
       2. padding : 내용과 테두리 사이의 간격. 패딩은 눈에 보이지 않음.
       3. border : 내용와 패딩 주변을 감싸는 테두리.
       4. margin : 테두리와 이웃하는 요소 사이의 간격. 마진은 눈에 보이지 않음.

- `float` 속성은 왜 좋지 않을까요?

  > 'float'를 이용한 레이아웃을 작성할때, 부모 요소가 자식 요소의 크기를 반영하지 못하는 문제가 발생.

- Flexbox(Flexible box)와 CSS Grid의 차이와 장단점은 무엇일까요?

  > flex는 1차원 레이아웃 시스템(수직, 수평중 택1) 이고 grid는 2차원 레이아웃 시스템(수직, 수평 둘 다 가능)으로 분류. grid는 항목을 두 방향으로 레이아웃 할 수있는 반면 flex는 한 방향만 할 수 있음. 간단한 레이아웃, 모바일 레이아웃 작업에는 flex를,복잡한 레이아웃 설계가 필요할 때 grid를 사용하면 좋음.

- CSS의 비슷한 요소들을 어떤 식으로 정리할 수 있을까요?
  > 그룹화 : 여러 개의 클래스 값을 사용하는 경우에, 이들 중 일부 몇 클래스만 동일한 스타일을 적용시키고 싶다면, 그룹으로 묶어서 관리 가능.

## Quest

- Quest 01에서 만들었던 HTML을 바탕으로, [이 그림](screen.png)의 레이아웃과 CSS를 최대한 비슷하게 흉내내 보세요. 꼭 완벽히 정확할 필요는 없으나 align 등의 속성은 일치해야 합니다.
- **주의사항: 되도록이면 원래 페이지의 CSS를 참고하지 말고 아무것도 없는 백지에서 시작해 보도록 노력해 보세요!**

## Advanced

- 왜 CSS는 어려울까요?
- CSS의 어려움을 극복하기 위해 어떤 방법들이 제시되고 나왔을까요?
- CSS가 브라우저에 의해 해석되고 적용되기까지 내부적으로 어떤 과정을 거칠까요?
- 웹 폰트의 경우에는 브라우저 엔진 별로 어떤 과정을 통해 렌더링 될까요?
