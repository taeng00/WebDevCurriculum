# Quest 19-F. 웹 어셈블리의 기초

## Introduction

- 이번 퀘스트에서는 2021년 현재 웹 프론트엔드의 많은 최신 기술 중 웹 어셈블리에 관해 알아보겠습니다.

## Topics

- Web Assembly
- Rust

## Resources

- [MDN - 웹어셈블리의 컨셉](https://developer.mozilla.org/ko/docs/WebAssembly/Concepts)
- [MDN - Rust to wasm](https://developer.mozilla.org/ko/docs/WebAssembly/Rust_to_wasm)
- [Learn Rust](https://www.rust-lang.org/learn)
- [Rust - sha2](https://docs.rs/sha2/0.9.5/sha2/)

## Checklist

- 웹 어셈블리란 어떤 기술인가요?

  > - 최신 웹브라우저에서 실행할 수 있는 새로운 유형의 코드를 말하며, C/C++/Rust 등 저급언어(기계어에 가까운 언어)를 효과적으로 컴파일링 하기 위해 고안된 기술.
  > - 기계어 컴파일링을 통해 네이티브 코드에 가까운 실행 속도를 구현할 수 있으며, Webassembly 모듈을 node.js로 가져와 Javascript 언어를 통해 해당 기능 사용 가능.
  > - 다만 npm에서는 Wasm이 아직 없으므로, 다른 코드에서 참조하는 방식으로 작성해야 함.

- 웹 어셈블리 모듈을 웹 프론트엔드 상에서 실행시키려면 어떻게 해야 할까요?

  > - Rust 등을 통해 작성한 언어를 Wasm으로 출력하면 js, wasm 파일이 생성됨.
  > - js에서 Wasm을 불러오면 Wasm은 javascript를 통해 제어가 가능하므로, 해당 환경에서 실행 및 작동이 가능해짐.
  > - 이 외에도 C/C++ 언어로 포팅(다른 환경에서 이해할 수 있는 언어로 작성)하거나, Wasm 바이너리 컴파일 등으로 Wasm을 사용 가능.

- Rust란 어떤 특징을 가진 프로그래밍 언어인가요?

  > 네이티브에 준하는 속도와 메모리 효율성(GC), 컴파일 과정에서의 버그 최소화 등을 목표로 고안된 현대적인 프로그래밍 언어.

- 웹 어셈블리 모듈을 만드는 방법에는 어떤 것들이 있나요?

  > go, rust, C/C++ 등으로 wasm 파일(패키지) 생성 가능.

- 웹 어셈블리가 할 수 없는 작업에는 무엇이 있을까요? 웹 어셈블리는 어떤 목적에 주로 쓰이게 될까요?

  > - web api에 접근 불가.
  > - 3d, 2d 그래픽 작업이나 기타 복잡한 연산이 필요한 경우에 사용.

## Quest

- 텍스트 에디터 프로그램에서 각 탭의 내용의 SHA-256 해시를 실시간으로 계산하여 화면 아래에 표시해 보세요.
  - 해당 해시는 Rust로 작성된 웹 어셈블리 함수를 통해 계산되어야 합니다.
  - 순수 자바스크립트로 계산할 때와의 퍼포먼스 차이를 체크해 보세요. (퍼포먼스 차이를 알아보는 데에 어떤 전략들이 있을까요?)

## Advanced

- 웹 어셈블리 바이너리는 어떻게 구성되어 있을까요?
