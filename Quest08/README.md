# Quest 08. 웹 API의 기초

## Introduction

- 이번 퀘스트에서는 웹 API 서버의 기초를 알아보겠습니다.

## Topics

- HTTP Method
- node.js `http` module
  - `req`와 `res` 객체

## Resources

- [MDN - Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN - MIME Type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
- [HTTP Node.js Manual & Documentation](https://nodejs.org/api/http.html)

## Checklist

- HTTP의 GET과 POST 메소드는 어떻게 다른가요?

  > - 사용목적 : GET은 서버의 리소스에서 데이터를 요청할 때, POST는 서버의 리소스를 새로 생성하거나 업데이트할 때 사용. DB로 따지면 GET은 SELECT 에 가깝고, POST는 Create 에 가깝다고 보면 됨.
  > - 요청에 body 유무 : GET 은 URL 파라미터에 요청하는 데이터를 담아 보내기 때문에 HTTP 메시지에 body가 없음. POST 는 body 에 데이터를 담아 보내기 때문에 당연히 HTTP 메시지에 body가 존재.
  > - 멱등성 ( 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질) : GET 요청은 멱등이며, POST는 멱등이 아님.

- 다른 HTTP 메소드에는 무엇이 있나요?

      - GET : 서버로 부터 데이터를 취득
      - POST : 서버에 데이터를 추가, 작성 등
      - PUT : 서버의 데이터를 갱신, 작성 등
      - DELETE : 서버의 데이터를 삭제
      - HEAD : 서버 리소스의 헤더(메타 데이터의 취득)
      - OPTIONS : 리소스가 지원하고 있는 메소드의 취득
      - PATCH : 리소스의 일부분을 수정
      - CONNECT : 프록시 동작의 터널 접속을 변경

- HTTP 서버에 GET과 POST를 통해 데이터를 보내려면 어떻게 해야 하나요?

- HTTP 요청의 `Content-Type` 헤더는 무엇인가요?

  > - Content-type이란 간단히 말해 보내는 자원의 형식을 명시하기 위해 헤더에 실리는 정보 . 이 값은 표준 mime-type중의 하나.

- Postman에서 POST 요청을 보내는 여러 가지 방법(`form-data`, `x-www-form-urlencoded`, `raw`, `binary`) 각각은 어떤 용도를 가지고 있나요?

       - `form-data` : 양식을 채울 때 입력 한 세부 정보와 같이 양식 내부에 래핑하는 데이터를 보내는 데에 사용. 이러한 세부 정보는 키가 보내는 항목의 '이름'이고, 값이 그 값인 KEY-VALUE 쌍으로 작성하여 전송됨.
       - `x-www-form-urlencoded` : `form-data`와 매우 유사. 차이점은 URL이 `x-www-form-urlencoded`를 통해 전송 될 때 인코딩 된다는 것. 인코딩 됨은 전송되는 데이터가 다른 문자로 인코딩 되어 공격을 받고 있어도 인식 할 수 없음을 의미.
       - `raw` : POST 메서드에서 본문을 보내는 동안 가장 많이 사용되는 부분 또는 옵션. Postman의 관점에서 중요한데, 원시는 본문 메시지가 요청 본문을 나타내는 비트 스트림으로 표시됨을 의미. 이러한 비트는 문자열 서버로 해석됨.
       - `binary` : 수동으로 입력 할 수 없는 형식으로 정보를 전송하도록 설계. 컴퓨터의 모든 것이 바이너리로 변환 되기 때문에 이미지, 파일 등과 같이 수동으로 작성할 수 없는 이러한 옵션을 사용.

- node.js의 `http` 모듈을 통해 HTTP 요청을 처리할 때, `req`와 `res` 객체에는 어떤 정보가 담겨있을까요?

       - `req` : req 개체는 HTTP 요청을 나타내며 요청 쿼리 문자열, 매개 변수, 본문, HTTP 헤더 등에 대한 속성을 가짐. 이 설명서 및 관례상 개체는 항상 req(그리고 HTTP 응답은 res)로 표시되지만 실제 이름은 작업 중인 콜백 함수에 대한 매개 변수에 의해 결정됨.
       - `res` : res 개체는 Express 앱이 HTTP 요청을 받을 때 보내는 HTTP 응답을 나타냄. 개체를 항상 res(그리고 HTTP 요청은 req)라고 부르지만 실제 이름은 작업 중인 콜백 함수에 대한 매개 변수에 의해 결정됨.

- GET과 POST에 대한 처리 형태가 달라지는 이유는 무엇인가요?
- 만약 API 엔드포인트(URL)가 아주 많다고 한다면, HTTP POST 요청의 `Content-Type` 헤더에 따라 다른 방식으로 동작하는 서버를 어떻게 정리하면 좋을까요?
- 그 밖에 서버가 요청들에 따라 공통적으로 처리하는 일에는 무엇이 있을까요? 이를 어떻게 정리하면 좋을까요?

## Quest

- 다음의 동작을 하는 서버를 만들어 보세요.
  - 브라우저의 주소창에 `http://localhost:8080`을 치면 `Hello World!`를 응답하여 브라우저에 출력합니다.
  - 서버의 `/foo` URL에 `bar` 변수로 임의의 문자열을 GET 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/foo` URL에 `bar` 키에 임의의 문자열 값을 갖는 JSON 객체를 POST 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/pic/upload` URL에 그림 파일을 POST 하면 서버에 보안상 적절한 방법으로 파일이 업로드 됩니다.
  - 서버의 `/pic/show` URL을 GET 하면 브라우저에 위에 업로드한 그림이 뜹니다.
  - 서버의 `/pic/download` URL을 GET 하면 브라우저에 위에 업로드한 그림이 `pic.jpg`라는 이름으로 다운로드 됩니다.
- expressJS와 같은 외부 프레임워크를 사용하지 않고, node.js의 기본 모듈만을 사용해서 만들어 보세요.
- 처리하는 요청의 종류에 따라 공통적으로 나타나는 코드를 정리해 보세요.

## Advanced

- 서버가 파일 업로드를 지원할 때 보안상 주의할 점에는 무엇이 있을까요?
