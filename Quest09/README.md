# Quest 09. 서버와 클라이언트의 대화

## Introduction

- 이번 퀘스트에서는 서버와 클라이언트의 연동, 그리고 웹 API의 설계 방법론 중 하나인 REST에 대해 알아보겠습니다.

## Topics

- expressJS, fastify
- AJAX, `XMLHttpRequest`, `fetch()`
- REST, CRUD
- CORS

## Resources

- [Express Framework](http://expressjs.com/)
- [Fastify Framework](https://www.fastify.io/)
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [REST API Tutorial](https://restfulapi.net/)
- [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

## Checklist

- 비동기 프로그래밍이란 무엇인가요?

  > 특정 코드의 처리가 완료되기 전, 처리하는 도중에도 아래로 계속 내려가며 수행을 하는 것

- 콜백을 통해 비동기적 작업을 할 때의 불편한 점은 무엇인가요? 콜백지옥이란 무엇인가요?

  > - 콜백 방식이란 비동기 작업이 완료되면 콜백함수를 호출하는 방법. 콜백함수란 순차적으로 실행하고 싶을 때 사용하는 것.
  > - 함수안에 함수, 또 그 함수안에 함수, 또 그 함수안에 함수, 또 그 함수안에..... 콜백을 사용하게 되면 이렇게 정말 복잡한 구조를 가진 콜백지옥이 완성될 수 있음. 이것은 가독성도 떨어지고 실수 위험도 커지기 때문에 말그대로 지옥이 될 수 있음.

- 자바스크립트의 Promise는 어떤 객체이고 어떤 일을 하나요?

  > Promise는 생성자에 인자로 들어가는 함수에 첫 번째 인자로는 수행할 비동기 작업, 두 번째 인자로는 그 결과물을 콜백함수에 전달하는 함수가 들어감.

- 자바스크립트의 `async`와 `await` 키워드는 어떤 역할을 하며 그 정체는 무엇일까요?

  > async함수안에 await로 지정한 비동기 함수를 사용하면, 해당 작업이 완료되기 전까진 다음으로 넘어가지 않음.

- 브라우저 내 스크립트에서 외부 리소스를 가져오려면 어떻게 해야 할까요?

  > http 프로토콜에서 req 인자에 외부 resource, data를 전달.

- 브라우저의 `XMLHttpRequest` 객체는 무엇이고 어떻게 동작하나요?

  > - `XMLHttpRequest` 객체는 서버로부터 XML 데이터를 전송받아 처리하는 데 사용
  > - 이 객체를 사용하면 웹 페이지가 전부 로딩된 후에도 서버에 데이터를 요청하거나 서버로부터 데이터를 전송받을 수 있음. 즉, 웹 페이지 전체를 다시 로딩하지 않고 일부분만을 갱신할 수 있게 됨.

- `fetch` API는 무엇이고 어떻게 동작하나요?

  > - fetch는 Promise의 단점을 보완한 최신 문법으로, 특정 URL로부터 데이터를 불러오는데 사용하는 API. 비동기 통신 중 하나이며, Promise 객체를 return하기에 사용하기 편함.

- REST는 무엇인가요?

  > - REST(Representational State Transfer)의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것을 의미.
  > - HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미.

- REST API는 어떤 목적을 달성하기 위해 나왔고 어떤 장점을 가지고 있나요?

      장점
      HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구출할 필요가 없음.
      HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해줌.
      HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능.
      Hypermedia API의 기본을 충실히 지키면서 범용성을 보장.
      REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악 가능.
      여러가지 서비스 디자인에서 생길 수 있는 문제를 최소화.
      서버와 클라이언트의 역할을 명확하게 분리.

- RESTful한 API 설계의 단점은 무엇인가요?

      단점
      표준, 스키마가 없다. 결국은 API 문서가 만들어지는 이유.
      행위에 대한 메소드가 제한적. (GET, POST, PUT, DELETE, HEAD, ...)
      브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 값이 왠지 더 어렵게 느껴짐.
      구형 브라우저가 아직 제대로 지원해주지 못하는 부분이 존재한다.
        - PUT, DELETE를 사용하지 못하는 점
        - pushState를 지원하지 않는 점

- CORS란 무엇인가요? 이러한 기능이 왜 필요할까요? CORS는 어떻게 구현될까요?

  > CORS(Cross-Origin Resource Sharing) : 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제.

      - 프리플라이트 요청 (Preflight Request)
      - 단순 요청 (Simple Request)
      - 인증정보 포함 요청 (Credentialed Request)

## Quest

- 이번 퀘스트는 Midterm에 해당하는 과제입니다. 분량이 제법 많으니 한 번 기능별로 세부 일정을 정해 보고, 과제 완수 후에 그 일정이 얼마나 지켜졌는지 스스로 한 번 돌아보세요.
  - 이번 퀘스트부터는 skeleton을 제공하지 않습니다!
- Quest 05에서 만든 메모장 시스템을 서버와 연동하는 어플리케이션으로 만들어 보겠습니다.
  - 클라이언트는 `fetch` API를 통해 서버와 통신합니다.
  - 서버는 8000번 포트에 REST API를 엔드포인트로 제공하여, 클라이언트의 요청에 응답합니다.
  - 클라이언트로부터 온 새 파일 저장, 삭제, 다른 이름으로 저장 등의 요청을 받아 서버의 로컬 파일시스템을 통해 저장되어야 합니다.
    - 서버에 어떤 식으로 저장하는 것이 좋을까요?
  - API 서버 외에, 클라이언트를 띄우기 위한 서버가 3000번 포트로 따로 떠서 API 서버와 서로 통신할 수 있어야 합니다.
  - Express나 Fastify 등의 프레임워크를 사용해도 무방합니다.
- 클라이언트 프로젝트와 서버 프로젝트 모두 `npm i`만으로 디펜던시를 설치하고 바로 실행될 수 있게 제출되어야 합니다.
- 이번 퀘스트부터는 앞의 퀘스트의 결과물에 의존적인 경우가 많습니다. 제출 폴더를 직접 만들어 제출해 보세요!

## Advanced

- `fetch` API는 구현할 수 없지만 `XMLHttpRequest`로는 구현할 수 있는 기능이 있을까요?
- REST 이전에는 HTTP API에 어떤 패러다임들이 있었을까요? REST의 대안으로는 어떤 것들이 제시되고 있을까요?
