# Quest 17-F. 번들링과 빌드 시스템

## Introduction

- 이번 퀘스트에서는 현대적 웹 클라이언트 개발에 핵심적인 번들러와 빌드 시스템의 구조와 사용 방법에 대해 알아보겠습니다.

## Topics

- Webpack
- Bundling
  - Data URL
- Transpiling
  - Source Map
- Hot Module Replacement

## Resources

- [Webpack](https://webpack.js.org/)
- [Webpack 101: An introduction to Webpack](https://medium.com/hootsuite-engineering/webpack-101-an-introduction-to-webpack-3f59d21edeba)

## Checklist

- 여러 개로 나뉘어진 자바스크립트나 이미지, 컴포넌트 파일 등을 하나로 합치는 작업을 하는 것은 성능상에서 어떤 이점이 있을까요?

> - 웹 서비스에서 랜더링 시 소요시간 감소
>   웹페이지 요청에 필요한 정적자산(Javascript, CSS 등)의 크기를 줄일 수 있어 최초 화면 랜더링 시 HTTP 통신 소요시간을 줄여줄 수 있음.
>   단, 동일한 자산을 요구하는 동일한 페이지 및 사이트에서는 번들링이 효과가 없을 수 있음.

> - 정적 자산에 대한 유효성 검사 소요시간 감소
>   브라우저는 각 자산에 대한 유효성 검사를 추가적으로 필요로 함.
>   이때 검사해야 할 파일의 개수가 줄어들면, 그만큼 유효성 검사 대상 파일 크기가 작아지므로 번들링을 통한 성능 개선 가능.

- 이미지를 Data URL로 바꾸어 번들링하는 것은 어떤 장점과 단점이 있을까요?

- Source Map이란 무엇인가요? Source Map을 생성하는 것은 어떤 장점이 있을까요?

> - 빌드한 파일과 원본 리소스를 서로 연결하여 디버깅 간 편의성을 제공해주는 도구.
>   Webpack을 통한 번들링(대부분 빌드와 번들링은 동일한 개념으로 취급)을 하면서 오류가 발생할 경우, 빌드를 완료한 후 오류를 감지(동적감지).
>   Source Map을 활용하면 원본 리소스와 연결이 되어, 오류가 발생한 파일 및 라인을 감지해낼 수 있음(정적감지).

- Webpack의 필수적인 설정은 어떤 식으로 이루어져 있을까요?

  > - Entry : webpack이 번들(빌드)를 시작하는 지점이자 경로.
  > - Output : entry 객체에 정의된 번들 항목(경로)을 묶은 후, 최종 결과물을 반환할 위치. entry 객체를 통해 모듈을 로딩하고 하나의 파일로 묶음.
  > - Loader : Webpack이 기존 번들할 수 있는 속성(Javascript, JSON)뿐만 아니라, HTML/CSS/Image 등 까지 번들할 수 있도록 관련 기능을 지원.
  > - Plugin : Webpack의 기본적인 동작 외 추가적인 기능을 제공. 결과물의 형태를 바꿔주는 기능을 제공하는데, 번들 최적화/환경 변수 주입 등의 작업을 Plugin을 통해 수행할 수 있음.

- Webpack의 플러그인과 모듈은 어떤 역할들을 하나요?

  > - 기존 브라우저에서 모듈을 완벽히 지원하지 못하여 이를 보완하기 위해 Webpack에서 제공하는 기능

- Webpack을 이용하여 HMR(Hot Module Replacement) 기능을 설정하려면 어떻게 해야 하나요?

  > webpack.config.js의 hot 옵션 true 지정.

## Quest

- 직전 퀘스트의 소스만 남기고, Vue의 Boilerplating 기능을 쓰지 않고 Webpack 관련한 설정을 원점에서 다시 시작해 보세요.
  - 필요한 번들링과 Source Map, HMR 등의 기능이 모두 잘 작동해야 합니다.

## Advanced

- Webpack 이전과 이후에는 어떤 번들러가 있었을까요? 각각의 장단점은 무엇일까요?
