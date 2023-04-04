# Quest 05. OOP 특훈

## Introduction

- 이번 퀘스트에서는 바닐라 자바스크립트의 객체지향 프로그래밍을 조금 더 훈련해 보겠습니다.

## Topics

- Separation of Concerns
- 객체지향의 설계 원칙
  - SOLID 원칙
- Local Storage

## Resources

- [Separation of concerns](https://jonbellah.com/articles/separation-of-concerns/)
- [SOLID](https://en.wikipedia.org/wiki/SOLID)
- [객체지향 설계 5원칙](https://webdoli.tistory.com/210)
- [MDN - Local Storage](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage)

## Checklist

- 관심사의 분리 원칙이란 무엇인가요? 웹에서는 이러한 원칙이 어떻게 적용되나요?

  > - 정의 : 소프트웨어 개발에서 가장 기본적인 원칙 중 하나이며, SOLID 원칙 5개 중 2개(단일 책임 및 인터페이스 분리)가 이 개념에서 직접 파생될 정도로 매우 중요.
  > - 프로그램을 하나의 단일 블록으로 작성하지 않고 작은 조각으로 나누어 각각 간단한 개별 작업을 완료할 수 있도록 만드는 것.

- 객체지향의 SOLID 원칙이란 무엇인가요? 이 원칙을 구체적인 예를 들어 설명할 수 있나요?

  > - Single Responsiblity Principle (단일 책임 원칙) - 소프트웨어의 설계 부품(클래스, 함수 등)은 단 하나의 책임만을 가져야 함.
  > - Open-Closed Principle (개방-폐쇄 원칙) - 기존의 코드를 변경하지 않고(Closed) 기능을 수정하거나 추가할 수 있도록(Open) 설계해야 함.
  > - Liskov Substitution Principle (리스코프 치환 원칙) - 자식 클래스는 부모클래스에서 가능한 행위를 수행할 수 있어야 함.
  > - Interface Segregation Principle (인터페이스 분리 원칙) - 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 함. 하나의 일반적인 인터페이스보다는, 여러 개의 구체적인 인터페이스가 나음.
  > - Dependency Inversion Principle (의존 역전 원칙) - 의존 관계를 맺을 때, 변화하기 쉬운것 보단 변화하기 어려운 것에 의존해야 한다는 원칙.

  > - 위 다섯가지의 맨 앞자를 따서 SOLID.

- 로컬 스토리지란 무엇인가요? 로컬 스토리지의 내용을 개발자 도구를 이용해 확인하려면 어떻게 해야 할까요?

  > - 로컬스토리지는 사용자의 로컬에 존재하는 저장소.
  >
  > 1. 크롬 브라우저에서 'F12' 키를 이용하여, 크롬 브라우저 개발자 도구를 오픈.
  > 2. 'Application' 탭을 선택.
  > 3. Storage > local Storage 영역에서 확인하고자 하는 도메인을 선택하면, 해당 도메인의 로컬스토리지 값을 확인할 수 있음.

## Quest

- 외부 라이브러리나 프레임워크를 사용하지 않고, 자바스크립트를 이용하여 간단한 웹브라우저 기반의 텍스트 에디터를 만들어 보겠습니다.
  - 기본적으로 VSCode와 같이 탭을 이용해 여러 개의 파일을 동시에 편집할 수 있습니다.
  - 탭을 눌러 열려 있는 다른 파일을 편집할 수 있으며 탭을 언제든지 닫을 수 있습니다.
  - VSCode와 같이 새 파일, 로드, 저장, 다른 이름으로 저장 등의 기능을 가집니다. 저장은 웹 브라우저의 로컬 스토리지를 이용합니다.
  - VSCode와 같이 탭이 수정되었는데 저장되기 이전일 경우 이를 알려주는 인디케이터가 작동합니다.
  - 같은 이름의 파일을 저장할 경우 에러를 표시해야 합니다.
- 이번 퀘스트의 결과물은 앞으로의 많은 퀘스트에서 재사용되게 되니, 주의깊게 코드를 작성해 보세요!

## Advanced

- 웹 프론트엔드 개발에서 이러한 방식의 패턴을 더 일반화해서 정리할 수 있을까요? 이 퀘스트에서 각각의 클래스들이 공통적으로 수행하게 되는 일들에는 무엇이 있을까요?
