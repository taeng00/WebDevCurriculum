# Quest 12. 보안의 기초

## Introduction

- 이번 퀘스트에서는 가장 기초적인 웹 서비스 보안에 대해 알아보겠습니다.

## Topics

- XSS, CSRF, SQL Injection
- HTTPS, TLS

## Resources

- [The Basics of Web Application Security](https://martinfowler.com/articles/web-security-basics.html)
- [Website Security 101](https://spyrestudios.com/web-security-101/)
- [Web Security Fundamentals](https://www.shopify.com.ng/partners/blog/web-security-2018)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [Wikipedia - TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)

## Checklist

- 입력 데이터의 Validation을 웹 프론트엔드에서 했더라도 서버에서 또 해야 할까요? 그 이유는 무엇일까요?

  > - client level에서 전달되는 data들은 데이터 위변조가 쉽고 그만큼 보안적으로 취약. 사용자, 혹은 이에 준하는 중요한 데이터들이 server에 안전하게 보관되기 위해선 client level의 validation보다 더 안전하고 신뢰할 수 있는 validation이 진행되어야 함.
  > - validation이라는 개념은 데이터의 유효성/ 신뢰도/ 위변조 여부 등 매우 넓은 범위를 포괄하며, 이는 경중에 따라 client - server side에서 처리하도록 분할할 수 있음.

- 서버로부터 받은 HTML 내용을 그대로 검증 없이 프론트엔드에 innerHTML 등을 통해 적용하면 어떤 문제점이 있을까요?

  > - server는 기본적으로 동적으로 명령을 수행(ASP, Active Server-side Page). server가 우리에게 보내는 data는 client의 요청/상황에 따라 다름.
  > - 다만 data를 보내는 틀(template, 디자인)은 보통은 정해져 있음. 이때 server의 data와 동작은 우리에게 보여지지 않는 반면, template은 보여짐.
  > - 그만큼 중요한 server side script는, 또다른 위변조(혹은 악의적으로 script를 편집하여 사용자 data로의 접근)가 발생하면 페이지 동작 자체에 영향을 미쳐 피해가 더 커질 수 밖에 없음.
  > - 예를 들어 server side script에서 다른 사용자의 정보를 훔쳐볼 수 있는 미들웨어가 삽입되었다면, 꼼짝없이 사용자 정보가 노출(=XSS).

- XSS(Cross-site scripting)이란 어떤 공격기법일까요?

  > - 웹사이트 간의 정보교환을 진행하면서 발생할 수 있는 악의적인 정보탈취.

        - 사용자의 동작, 행위에서 비롯되는 공격으로 사용자가 특정 웹사이트를 신뢰하는 상황에서 많이 발생.
        - 악의적으로 다른 사이트에서의 데이터를 탈취하기위해, 정보를 훔쳐오기위한 logic(script)을 server-side에 작성하는 행위.
        - 웹 어플리케이션에서 사용자가 입력한 값의 유효성을 판단해야 하는 이유 중 하나이며, 이 공격에 노출되면 사용자가 의도하지 않은 동작을 수행하거나 관련 쿠키 정보 등이 탈취됨.

- CSRF(Cross-site request forgery)이란 어떤 공격기법일까요?

  > XSS와 마찬가지로 웹사이트 간의 정보교환을 진행하면서 발생하는 정보탈취 이며, 사용자가 웹 브라우저를 통해 사이트에 공격을 요청(request)하도록 유도하는 행위

- SQL Injection이란 어떤 공격기법일까요?

  > SQL을 통한 감염, 악의적으로 SQL query를 조작하여 데이터베이스를 도용하거나 무단으로 조회하는 행위. 기본적으로 사용자가 입력한 값을 검증해야 하는 이유이기도 함.

- 대부분의 최신 브라우저에서는 HTTP 대신 HTTPS가 권장됩니다. 이유가 무엇일까요?
  - HTTPS와 TLS는 어떤 식으로 동작하나요? HTTPS는 어떤 역사를 가지고 있나요?
  - HTTPS의 서비스 과정에서 인증서는 어떤 역할을 할까요? 인증서는 어떤 체계로 되어 있을까요?

## Quest

- 메모장의 서버와 클라이언트에 대해, 로컬에서 발행한 인증서를 통해 HTTPS 서비스를 해 보세요.

## Advanced

- TLS의 인증서에 쓰이는 암호화 알고리즘은 어떤 종류가 있을까요?
- HTTP/3은 기존 버전과 어떻게 다를까요? HTTP의 버전 3이 나오게 된 이유는 무엇일까요?
