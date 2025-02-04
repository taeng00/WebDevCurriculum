# Quest 04. OOP의 기본

## Introduction

- 이번 퀘스트에서는 바닐라 자바스크립트의 객체지향 프로그래밍에 대해 알아볼 예정입니다.

## Topics

- 객체지향 프로그래밍
  - 프로토타입 기반 객체지향 프로그래밍
  - 자바스크립트 클래스
    - 생성자
    - 멤버 함수
    - 멤버 변수
  - 정보의 은폐
  - 다형성
- 코드의 재사용

## Resources

- [MDN - Classes](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)
- [MDN - Inheritance and the prototype chain](https://developer.mozilla.org/ko/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [MDN - Inheritance](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Inheritance)
- [Polymorphism](https://medium.com/@viktor.kukurba/object-oriented-programming-in-javascript-3-polymorphism-fb564c9f1ce8)
- [Class Composition](https://alligator.io/js/class-composition/)
- [Inheritance vs Composition](https://woowacourse.github.io/javable/post/2020-05-18-inheritance-vs-composition/)

## Checklist

- 객체지향 프로그래밍은 무엇일까요?

  > 어떤 개념에 대한 자료형과 함수를 객체 형태로 함께 묶어서 관리하기 위해 객체지향 프로그래밍 등장. 객체 내부에 자료형 필드와 함수가 함께 존재하는 것. 가능한 모든 물리적, 논리적 요소를 객체로 만드는 것이 객체지향 프로그래밍.

- `#`로 시작하는 프라이빗 필드는 왜 필요한 것일까요?

  > `#` ES2019부터 추가된 기능, 캡슐화를 구현하여 해당 필드에 접근할 수 있는 권한을 클래스 외부로부터 제한, 정보를 은폐 할 수 있음.

- 정보를 은폐(encapsulation)하면 어떤 장점이 있을까요?

  > - 코드가 구체적인 것들(타입, 메소드, 구현)에 의존하는 것을 막아줌 으로서 객체 간의 구체적인 결합도를 약화시켜 기능의 교체나 변경이 쉽도록 함.
  > - 동일한 타입의 다른 구현 객체들을 교체함 으로서 동적 기능 변경이 가능함.
  > - 연동할 구체적인 구현이 없는 상태에서도 (인터페이스 만으로) 정확한 연동 코드의 생성이 가능함.

- 다형성이란 무엇인가요? 다형성은 어떻게 코드 구조의 정리를 도와주나요?

  > - 어떤 객체의 속성이나 기능이 상황에 따라 여러 가지 형태를 가질 수 있는 성질을 의미.
  > - 반복된 코드를 줄이며 꼭 필요한 코드만 수정한다는 장점이 있음.

- 상속이란 무엇인가요? 상속을 할 때의 장점과 단점은 무엇인가요?

  > - 정의 : 객체가 다른 객체를 상속받아 상속받은 객체의 요소를 사용하는 것을 의미. 이 때 객체를 상속받은 객체는 자식, 상속된 개체는 부모라 칭함.
  > - 장점 : 코드의 재사용성을 높이고, 중복을 제거해서 프로그래밍 생산성과 유지보수에 크게 기여.
  > - 단점 : 캡슐화가 깨지고 결합도가 높아짐.유연성 및 확장성이 떨어짐. 다중상속에 의한 문제가 발생할 수 있음. 클래스 폭발 문제가 발생할 수 있음.

- OOP의 합성(Composition)이란 무엇인가요? 합성이 상속에 비해 가지는 장점은 무엇일까요?

  > - 정의 : 중복되는 로직들을 갖는 객체를 구현하고, 이 객체를 주입받아 중복 로직을 호출함으로써 퍼블릭 인터페이스를 재사용하는 방법.
  > - 장점 : 구현을 효과적으로 캡슐화 할 수 있음. 의존하는 객체를 교체하는 것이 비교적 쉬우므로 설계가 유연. 코드 재사용을 위해서는 상속보다 합성을 선호하는 것이 더 좋은 방법.

- 자바스크립트의 클래스는 어떻게 정의할까요?

  > class 표현식을 사용하면, 생성자와 같은 기능을 하는 함수를 훨씬 더 깔끔한 문법으로 정의할 수 있음.

- 프로토타입 기반의 객체지향 프로그래밍은 무엇일까요?

  > - 프로토타입 기반 언어 : 원형 객체를 복제하여 새로운 객체를 하는 생성하는 언어
  > - 자바스크립트는 약간 다름. 복제가 아닌 프로토타입 링크를 통해 원형을 참조.

- 자바스크립트의 클래스는 이전의 프로토타입 기반의 객체지향 구현과 어떤 관계를 가지고 있나요?

  > - 자바스크립트는 객체 지향 언어지만 기존의 클래스 기반 프로그래밍 방식을 따르지 않으며 프로토타입 기반 프로그래밍 방식으로 동작.
  > - 클래스 기반 언어에서의 클래스 : '객체의 상태와 기능을 정의한 틀'이며 생성될 객체에 대한 일종의 청사진으로 이해할 수 있음. 그리고 이것의 인스턴스 화를 통해 생성된 객체를 인스턴스. 여기서 인스턴스는 클래스에서 정의된 모든 특성에 대한 복사본이기 때문에 두 개념은 개별적이며 서로 간의 참조는 존재하지 않음.
  > - 프로토타입 기반 언어 : 클래스 - 인스턴스의 개념이 아닌 오직 객체 개념만 존재. ES6에 도입된 클래스 문법은 실제 클래스 패턴에 대한 모방일 뿐임. 이것은 자바스크립트의 생성자 함수 패턴을 좀 더 클래스답게 보이기 위한 장치이며 생성된 객체는 함수의 프로토타입 객체에 연결되어 있음.

## Quest

- 웹 상에서 동작하는 간단한 바탕화면 시스템을 만들 예정입니다.
- 요구사항은 다음과 같습니다:
  - 아이콘은 폴더와 일반 아이콘, 두 가지의 종류가 있습니다.
  - 아이콘들을 드래그를 통해 움직일 수 있어야 합니다.
  - 폴더 아이콘은 더블클릭하면 해당 폴더가 창으로 열리며, 열린 폴더의 창 역시 드래그를 통해 움직일 수 있어야 합니다.
  - 바탕화면의 생성자를 통해 처음에 생겨날 아이콘과 폴더의 개수를 받을 수 있습니다.
  - 여러 개의 바탕화면을 각각 다른 DOM 엘리먼트에서 동시에 운영할 수 있습니다.
  - Drag & Drop API를 사용하지 말고, 실제 마우스 이벤트(mouseover, mousedown, mouseout 등)를 사용하여 구현해 보세요!

## Advanced

- 객체지향의 역사는 어떻게 될까요?
- Smalltalk, Java, Go, Kotlin 등의 언어들로 넘어오면서 객체지향 패러다임 측면에서 어떤 발전이 있었을까요?
