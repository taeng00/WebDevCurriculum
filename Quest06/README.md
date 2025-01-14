# Quest 06. 인터넷의 이해

## Introduction

- 이번 퀘스트에서는 인터넷이 어떻게 동작하며, 서버와 클라이언트, 웹 브라우저 등의 역할은 무엇인지 알아보겠습니다.

## Topics

- 서버와 클라이언트, 그리고 웹 브라우저
- 인터넷을 구성하는 여러 가지 프로토콜
  - IP
  - TCP
  - HTTP
- DNS

## Resources

- [OSI 모형](https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95)
- [IP](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%84%B7_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Online service Traceroute](http://ping.eu/traceroute/)
- [TCP](https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EC%A0%9C%EC%96%B4_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Wireshark](https://www.wireshark.org/download.html)
- [HTTP](https://ko.wikipedia.org/wiki/HTTP)
  - Chrome developer tool, Network tab
- [DNS](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%EB%84%A4%EC%9E%84_%EC%8B%9C%EC%8A%A4%ED%85%9C)
  - [Web-based Dig](http://networking.ringofsaturn.com/Tools/dig.php)

## Checklist

- 인터넷은 어떻게 동작하나요? Internet Protocol Suite의 레이어 모델에 입각하여 설명해 보세요.

  > - 지역PC가 인터넷에 접근할때 인터넷 영역에서의 수많은 라우팅을 관리하는 Hob(Default Gateway)이 필요하며, 최종적으로 인터넷 사이트에 해당하는 라우터에 접근.
  > - 보통 상대의 목적지 IP 주소는 특정 값으로 정해지지만, 인터넷의 경우엔 0.0.0.0/0으로 특정지어지지 않음.
  > - 라우팅 경로 정보가 정해져있는 정적라우팅과는 달리, 네트워크 상황에 따라 정보를 빠르게 확보할 수 있는 경로를 중심으로 패킷을 전송하는 라우팅.
  > - 데이터 정보에 포함된 목적지 주소가 인터넷처럼 광범위하거나, 정적 라우팅을 통한 탐색이 불가능할 경우 동적 라우팅(보통 지역 통신사 등)을 통해 데이터 전달을 진행.

- 근거리에서 서로 떨어진 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?

  > - 근거리에 놓여진 두 기기의 네트워크 대역은 보통 정적 라우팅을 통해 연결, 라우팅테이블에 저장된 두 기기의 IP와 PORT 정보를 통해 데이터 전달이 이루어짐.
  > - 와이파이를 통해 연결한다면 무선 공유기를 통한 라우팅을 진행할 것이고, 블루투스를 통해 연결한다면 BLE stack 프로토콜을 기반으로 통신을 진행.

- 근거리에 있는 여러 대의 전자기기가 서로 통신하는 프로토콜은 어떻게 동작할까요?

  > - LAN 방식
  > - LAN(Local Area Network)은 보통 같은 사무실이나 공장, 연구소, 학교 등 비교적 가까운 지역 내에 분산 설치되어 있는 개인용 컴퓨터, 워크스테이션, 호스트 컴퓨터 등을 상호 접속하여 구성됨. 단지 가깝다는 거리 개념보다는 한 조직이 소유하는 인접 지역 내의 통신망을 LAN이라 함

- 아주 멀리 떨어져 있는 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?

  > - 사용하는 프로토콜은 두 기기간 거리보다는, 두 기기가 네트워크를 어떤 형태를 통해 연결하였으며 어떤 통신규약을 채용하고 있는지에 영향을 받음.
  > - 보통 멀리 떨어져 있는 기기의 경우엔 근거리 대역의 네트워크가 없어 라우팅 테이블 작성이 어려우므로, 인터넷과 같이 Hob(지역 통신사)를 통한 데이터 전달이 이루어짐.

- 두 전자기기가 신뢰성을 가지고 통신할 수 있도록 하기 위한 프로토콜은 어떻게 동작할까요?

  > - 웹과 사용자간의 대표적인 통신규약인 HTTP는, SSL인증을 적용한 HTTPS 프로토콜을 사용한 것이 가장 대표적인 보안적용의 예.
  > - HTTP프로토콜을 통한 데이터통신 과정에 SSL/TLS 암호화 방식(양방향 암호화)을 적용하여 상대적으로 안전한 데이터 전달이 가능하도록 한 방식.

- HTTP는 어떻게 동작할까요?

  > - 월드 와이드 웹의 토대이며 하이퍼텍스트 링크를 사용하여 웹 페이지를 로드하는 데 사용.
  > - 서버 접속 -> 클라이언트 -> 요청 -> 서버 -> 응답 -> 클라이언트 -> 연결 종료

      1. 사용자가 웹 브라우저에 URL 주소 입력
      2. DNS 서버에 웹 서버의 호스트 이름을 IP 주소로 변경 요청
      3. 웹 서버와 TCP 연결 시도 (3way- handshaking)
      4. 클라이언트가 서버에게 요청
      5. 서버가 클라이언트에게 데이터 응답
      6. 서버 클라이언트 간 연결 종료 (4way- handshaking)
      7. 웹 브라우저가 웹 문서 출력

- 우리가 브라우저의 주소 창에 www.knowre.com 을 쳤을 때, 어떤 과정을 통해 서버의 IP 주소를 알게 될까요?

      1. 브라우저는 DNS서버로 가서 도메인을 확인하고 웹사이트가 있는 서버의 IP주소를 탐색.
      2. 서버에게 웹사이트의 사본을 클라이언트에게 보내달라는 HTTP 요청 메시지를 서버로 전송.
      3. 서버는 클라이언트의 요청을 승인하고 웹 사이트의 정보를 패킷으로 묶어서 브라우저로 보냄.
      4. 브라우저는 이 패킷들을 활용하여 웹사이트로 만들어서 사용자에게 보여줌.

## Quest

- tracert(Windows가 아닌 경우 traceroute) 명령을 통해 www.google.com 까지 가는 경로를 찾아 보세요.

  - 어떤 IP주소들이 있나요?
  <p align="center">
    <img src="https://user-images.githubusercontent.com/124439821/230173341-bb022950-d495-4ff6-a73a-dfe64488b3e3.png">
  </p>

  - 그 IP주소들은 어디에 위치해 있나요?
    > hkg07s50-in-f4.1e100.net (맞나?)

- Wireshark를 통해 www.google.com 으로 요청을 날렸을 떄 어떤 TCP 패킷이 오가는지 확인해 보세요

  - TCP 패킷을 주고받는 과정은 어떻게 되나요?
    > 3way- handshaking
  - 각각의 패킷에 어떤 정보들이 담겨 있나요?
    > Source Port (발신지 포트 필드), Destination Port (목적지 포트 필드), Sequence Number (순차 번호 필드), Acknowledgement Number (확인 응답 번호 필드), Header Length (데이터 오프셋 필드) 등등..

- telnet 명령을 통해 http://www.google.com/ URL에 HTTP 요청을 날려 보세요.
  - 어떤 헤더들이 있나요?
  - 그 헤더들은 어떤 역할을 하나요?

## Advanced

- HTTP의 최신 버전인 HTTP/3는 어떤 식으로 구성되어 있을까요?
- TCP/IP 외에 전세계적인 네트워크를 구성하기 위한 다른 방식도 제안된 바 있을까요?
