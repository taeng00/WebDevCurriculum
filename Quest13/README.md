# Quest 13. 웹 API의 응용과 GraphQL

## Introduction

- 이번 퀘스트에서는 차세대 웹 API의 대세로 각광받고 있는 GraphQL에 대해 알아보겠습니다.

## Topics

- GraphQL
  - Schema
  - Resolver
  - DataLoader
- Apollo

## Resources

- [GraphQL](https://graphql.org/)
- [GraphQL.js](http://graphql.org/graphql-js/)
- [DataLoader](https://github.com/facebook/dataloader)
- [Apollo](https://www.apollographql.com/)

## Checklist

- GraphQL API는 무엇인가요? REST의 어떤 단점을 보완해 주나요?

  > - GraphQL 은 Graph Query Language 의 줄임말. API서버에서 엄격하게 정의된 endpoint 들에 요청하는 대신, 한번의 요청으로 정확히 가져오고 싶은 데이터를 가져올 수 있게 도와주는 쿼리를 보낼수 있음.

      - REST에서는 Resource에 대한 형태 정의와 데이터 요청 방법이 연결되어 있지만, GraphQL에서는 Resource에 대한 형태 정의와 데이터 요청이 완전히 분리되어 있음.
      - REST에서는 Resource의 크기와 형태를 서버에서 결정하지만, GraphQL에서는 Resource에 대한 정보만 정의하고, 필요한 크기와 형태는 client단에서 요청 시 결정.
      - REST에서는 URI가 Resource를 나타내고 Method가 작업의 유형을 나타내지만, GraphQL에서는 GraphQL Schema가 Resource를 나타내고 Query, Mutation 타입이 작업의 유형을 나타냄.
      - REST에서는 여러 Resource에 접근하고자 할 때 여러 번의 요청이 필요하지만, GraphQL에서는 한번의 요청에서 여러 Resource에 접근할 수 있음.
      - REST에서 각 요청은 해당 엔드포인트에 정의된 핸들링 함수를 호출하여 작업을 처리하지만, GraphQL에서는 요청 받은 각 필드에 대한 resolver를 호출하여 작업을 처리.

- GraphQL 스키마는 어떤 역할을 하며 어떤 식으로 정의되나요?

  > - 스키마(Schema)란 데이터 타입의 집합. 스키마 정의는 API 문서 같은 역할을 하며, 프론트엔드 개발자와 백엔드 개발자가 많은 의사 소통에 대한 비용을 줄이고 빠른 개발을 할 수 있다는 장점이 있음. 백엔드 개발자는 어떤 데이터를 전달해야 하는지, 프론트엔드 개발자는 인터페이스 작업을 할 때 필요한 데이터를 정의할 수 있는 것.

- GraphQL 리졸버는 어떤 역할을 하며 어떤 식으로 정의되나요?

  > - 리졸버(resolver)란 스키마에 작성한 타입의 필드 값들을 정의한다. 즉, 특정 필드의 데이터를 반환하는 함수.
  > - 스키마는 객체를 리턴할 수도 있고, String, Int, Boolean 등과 같이 scalar 값들도 리턴할 수 있음. 객체가 리턴 될 경우에는 자식 필드(child field)로 체이닝 되면서 리졸버가 실행되고, scalar가 리턴 될 경우 실행이 완료된 것으로 간주.

- GraphQL 리졸버의 성능 향상을 위한 DataLoader는 무엇이고 어떻게 쓰나요?

  > - DataLoader는 N+1문제에서 발생하는 많은 수의 쿼리를 일괄 처리 및 캐싱 할 수 있도록 해주는 라이브러리.
  > - N+1 문제 : GraphQL은 데이터베이스로 데이터를 처리할때에 편리한 기능들을 제공. 하지만 대량의 데이터를 가져오는데에 연쇄 리졸버로 연관된 데이터를 쿼리를 하게된다면 쿼리에 대한 데이터가 N개이고 또 내부의 리졸버가 N번 만큼 발생하여 데이터베이스에 쿼리를 하게되면 발생하는 쿼리의 수는 N번 만큼 발생하게 됨.

- 클라이언트 상에서 GraphQL 요청을 보내려면 어떻게 해야 할까요?

  > - Apollo Client : GraphQL API를 호출할 때 사용하는 클라이언트 라이브러리
  > - Apollo Client란, 자바스크립트를 위한 상태 관리 라이브러리. GraphQL 쿼리를 작성하면서 Apollo Client는 데이터를 가져오고 캐싱을 해주고 UI를 업로드 해줌.

- Apollo 프레임워크(서버/클라이언트)의 장점은 무엇일까요?

  > - Apollo는 유연하고 러닝 커브가 높지 않을뿐더러 프론트엔드 프레임워크인 React, Agular, Vue를 동시에 지원. 특히 뷰에서 리엑트를 쓸 경우에 Redux를 Apollo로 대체가 가능.
  > - Apollo를 사용하면, GraphQL 서버에 쿼리, 뮤테이션, 리졸버를 작성하듯, 클라이언트 에서도 클라이언트 만의 Local state를 만들어 쿼리, 뮤테이션, 리졸버의 사용이 가능.

- Apollo Client를 쓰지 않고 Vanilla JavaScript로 GraphQL 요청을 보내려면 어떻게 해야 할까요?

  > - fetch, axios과 같은 데이터 전달 module 및 REST API(GET/POST method) 등 data를 확보할 수 있는 별도의 모듈을 사용해야 함.
  > - 변수가 담겨진 querystring 및 req.body와 같은 요소를 활용할 수 있음.

- GraphQL 기반의 API를 만들 때 에러처리와 HTTP 상태코드 등은 어떻게 하는게 좋을까요?

## Quest

- 메모장의 서버와 클라이언트 부분을 GraphQL API로 수정해 보세요.

## Advanced

- GraphQL이 아직 제대로 수행하지 못하거나 불가능한 요구사항에는 어떤 것이 있을까요?
- GraphQL의 경쟁자에는 어떤 것이 있을까요?
