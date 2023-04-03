# Quest 00. 형상관리 시스템

## Introduction

- git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics

- git
  - `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  - `.git` 폴더
- GitHub

## Resources

- [Resources to learn Git](https://try.github.io)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
- [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist

- 형상관리 시스템은 왜 나오게 되었을까요?

  > - 형상관리는 어떠한 문서나 파일이 변경된 경우, 변경된 내용과 그 원인을 기록하였다가 나중에 필요한 경우 찾아볼 수 있도록 하여 관리하는 것.
  > - 협업을 할 때는 더더욱이 필요한 것이, 변경사항이 쉽게 확인이 가능하고, 수정이 편리, 각 개인이 수정 중 충돌 방지 등의 기능이 있는 형상관리 시스템이 필요 하다.

- git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?

  > - git : 분산형 형상관리 시스템 이다.
  > - 특징 : 소스코드를 여러 개발 PC와 저장소에 분산해서 저장, 그렇기 때문에 중앙 서버에 장애가 발생해도 로컬 저장소에 커밋을 할 수 있으며, 로컬 저장소들을 이용하여 중앙 저장소의 복원도 가능하다.

- git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?

  > - 2005년에 커뮤니티가 만드는 Linux 커널과 이익을 추구하는 회사가 개발한 BitKeeper의 관계는 틀어졌다. BitKeeper의 무료 사용이 재고된 것이다. 이 사건은 Linux 개발 커뮤니티(특히 Linux 창시자 Linus Torvalds)가 자체 도구를 만드는 계기가 됐다.

- git과 GitHub은 어떻게 다를까요?

  > - 간단하게 git = 로컬에서 관리 되던 내용들, 코드, 로그 등등을 Github =(ex/ Google Drive)에 올리는 것

- git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?

  > - clone : 원격 레포지터리를 내 로컬에 그대로 복사 해 오는 것 ex) git clone https://github.com/Knowre-Dev/webDevCurriculum.git .
  > - add : commit을 기록할 때까지 변경분을 모아놓기 위한 동작. ex) git add 파일명
  > - commit : 작성, 수정등의 의미 있는 작업이 마무리 된 후 변화에 대해 기록하는 것 ex) git commit -m "저장될 이름?"
  > - pull : 원격 레포지터리를 가져와 현재 브랜치에 병합을 해줌, 기존의 작업내용은 그대로 유지 되면서 최신 코드로 업데이트. ex) git pull [원격 저장소 이름] [브랜치 이름]
  > - push : 변경 내용 들을 원격 레포지터리에 업로드. ex) git push -u origin
  > - stash : commit과는 다른 임시저장 같은 느낌?ex) git stash

- git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?

  > - commit : add된 파일들을 로컬 레포지에 변경 작업을 저장
  > - head : 해당 branch의 마지막 commit에 대한 포인터
  > - branch : 특정 장소(branch) 아래에 새로운 파일을 추가 한다거나 추가한 파일의 내용을 변경하여 그 내용을 commit 하는 것은 모두 해당 branch를 통해 처리할 수 있음.
  > - tag : 특정 commit을 태그 (특정 commit을 가리키는 링크). commit과 다르게 수정이 불가능하여 읽기 전용 commit같은 느낌

- 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
  > - git rm [파일 명] //원격 레포지와 로컬 레포지에 있는 파일 삭제
  > - git rm --cached [파일 명] //원격 레포지에 있는 파일 삭제

## Quest

- GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다.
- Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다.
  - 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다.
- 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다.
- `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다.

## Advanced

- Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
- 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
