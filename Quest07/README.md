# Quest 07. node.js의 기초

## Introduction

- 이번 퀘스트에서는 node.js의 기본적인 구조와 개념에 대해 알아 보겠습니다.

## Topics

- node.js
- npm
- CommonJS와 ES Modules

## Resources

- [About node.js](https://nodejs.org/ko/about/)
- [Node.js의 아키텍쳐](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174356/node-js%EC%9D%98-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90)
- [npm](https://docs.npmjs.com/about-npm)
- [npm CLI commands](https://docs.npmjs.com/cli/v7/commands)
- [npm - package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- [How NodeJS Require works!](https://www.thirdrocktechkno.com/blog/how-nodejs-require-works)
- [MDN - JavaScript Modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- [require vs import](https://www.geeksforgeeks.org/difference-between-node-js-require-and-es6-import-and-export/)

## Checklist

- node.js는 무엇인가요? node.js의 내부는 어떻게 구성되어 있을까요?

  > - node.js = Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임. 노드를 통해 다양한 자바스크립트 애플리케이션을 실행할 수 있으며, 서버를 실행하는 데 제일 많이 사용.

  <p align="center">
    <img src="https://user-images.githubusercontent.com/124439821/230406771-0fa09ad1-89d8-4de8-a1c7-346aca992536.png">
  </p>

  > - 가장 위는 일반적인 Javascript 코드. 그 밑으로는 NodeJS가 있는데 NodeJS 안에는 여러가지 기본모듈들(http, fs, crypto, path 등)이 존재. 모듈은 50%는 JS, 나머지 50%는 C++으로 되어있음.
  > - NodeJS는 2가지 의존성을 갖는데 V8과 libuv.

       - V8은 오픈소스 자바스크립트 엔진으로서 구글이 개발하여 크롬에서 쓰이고 있으며 브라우저 밖에서도 자바스크립트가 실행될 수 있도록 결정적인 역할을 했다.
       - libuv는 C++ 오픈소스 프로젝트로 NodeJS 가 OS에 접근하도록 또는 파일시스템과 네트워킹, 기타 다른것에 접근할 수 있는 모듈로 되어있음. 한마디로 NodeJS가 플랫폼 독립적인데 결정적인 역할.

- npm이 무엇인가요? `package.json` 파일은 어떤 필드들로 구성되어 있나요?

  > - Node Package Manager : node.js를 위한 패키지 매니저이자, node.js를 위한 오픈소스 생태계, node.js에서 사용하는 모듈들을 패키지로 만들어 관리하고 배포하고 있음.
  > - `package.json` : 개발자가 배포한 패키지에 대해, 다른 사람들이 관리하고 설치하기 쉽게 하기 위한 문서. npm에 패키지를 배포하고 npm registry에 올리기 위해서 반드시 필요한 문서파일.

  <p align="center">
    <img src="https://user-images.githubusercontent.com/124439821/230414984-5763245d-f246-4830-bb95-96c3f93b23d1.png">
  </p>

      "name" : 말그대로 이 패키지의 이름을 나타냄.
      "version": semantic versioning guidelines를 따르며, x.x.x의 형태로 작성해야 함.
      “description” :문자열로 기술한 패키지에 대한 설명. npm에서 검색되었을 때 리스트에 표시되어 사람들이 패키지를 찾아내고 이해할 수 있는데 도움.
      "main” : 패키지의 진입점(entry point)이 되는 모듈의 ID.
      “scripts” : 패키지의 생명주기에서 다양한 타이밍에 자주 사용할 command를 alias(별칭)을 통해 지정해 둘 수 있는 dictionary.
      “keywords” : 키워드를 문자열 배열로 설명. description과 마찬가지로 npm에서 검색되었을 때 리스트에 표시되어 사람들이 패키지를 찾아내고 이해할 수 있는데 도움.
      “author” : 배포자 한 사람을 위한 field로, 다수의 사람을 표시하기 위해서는 “contributors” field로 작성해야 함.
      “license” : 배포한 패키지에 대해 패키지 사용자가 패키지를 사용하는데 어떤 권한과 제한 사항이 있는지 알기 위해 license를 명시해야 함.

- npx는 어떤 명령인가요?

  > - Node Pacakage eXecution : 노드패키지의 실행에 중점을 둔 명령어.
  > - npm 5.2버전부터, npx가 기본 패키지로 제공되기 시작. npm의 영구적인 설치, 관리 등의 부가적인 절차없이 원하는 패키지를 npm 레지스트리에 접근시켜 실행만 할 수 있도록 설치하는 일종의 실행도구.
  > - 모듈을 로컬에 저장하지 않고, 매번 최신 버전의 파일만을 임시로 불러와 실행 시킨 후에, 다시 그 파일은 없어지는 방식.

- npm 패키지를 `-g` 옵션을 통해 글로벌로 저장하는 것과 그렇지 않은 것은 어떻게 다른가요?

  > - npm install -g <package>

      - node package를 전역적으로 설치하여, 말 그대로 PC내부에서의 프로젝트 전역적으로 참조할 수 있는 package가 설치됨.
      - window의 경우 전역 node_modules directory에 설치됨.

  > - npm install <package>

      - 설치 옵션을 별도로 지정하지 않을 경우엔 package가 지역적으로 설치됨, 해당 프로젝트 내부에서만 사용 가능.
      - 프로젝트 내부 디렉토리(지역적) node_modules에 설치되며, 실행파일 역시 지역적 디렉토리에 설치됨.

- CommonJS

  > - 자바스크립트를 서버에서 사용할 수 있는 큰 이유 중 하나는 모듈화가 가능하기 때문. 자바스크립트의 모듈화 명세를 만든 대표적인 그룹 중 'CommonJS'가 있고, 이 CommonJS의 명세가 현재 node의 표준.
  > - node 표준(=CommonJS의 명세)이 require와 module.exports

- ES Modules

  > - ES6로 넘어오면서 자바스크립트 자체에서 ES6 Module이라는 이름으로 모듈화를 지원하기 시작.
  > - import 와 export

- ES Modules는 기존의 `require()`와 동작상에 어떤 차이가 있을까요? CommonJS는 할 수 있으나 ES Modules가 할 수 없는 일에는 어떤 것이 있을까요?
- node.js에서 ES Modules를 사용하려면 어떻게 해야 할까요? ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면 어떻게 해야 할까요? 그 반대는 어떻게 될까요?

## Quest

- 스켈레톤 코드에는 다음과 같은 네 개의 패키지가 있으며, 용도는 다음과 같습니다:
  - `cjs-package`: CommonJS 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `esm-package`: ES Modules 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `cjs-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, CommonJS 기반의 프로젝트입니다.
  - `esm-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, ES Modules 기반의 프로젝트입니다.
- 각각의 패키지의 `package.json`과 `index.js` 또는 `index.mjs` 파일을 수정하여, 각각의 `*-my-project`들이 `*-package`에 노출된 함수와 클래스를 활용할 수 있도록 만들어 보세요.

## Advanced

- node.js 외의 자바스크립트 런타임에는 어떤 것이 있을까요?
