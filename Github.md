### Github
- 내 소스코드를 저장 ( 버전 관리 )
- 소스코드 공유
- 협업 공간

------

## GitKraken

Git명령어를 외우지 않고 사용이 가능한 GUI깃 클라이언트 프로그램

- GUI : 그래픽 사용자 인터페이스는 사용자가 편리하게 사용할 수 있도록 입출력 등의 기능을 알기 쉬운 아이콘등의 그래픽으로 나타낸 것

------

## 작업폴더 구성

fetch : 원격저장소의 내용을 가져오기

![images_danna-lee_post_b11e702a-f5a5-4e67-baee-5b918e10d26a_Slide5 (2)](https://user-images.githubusercontent.com/103401813/179659803-d7942998-02eb-4e4e-9340-db1a43ff2208.png)

추적(tracked) 여부

- 변화가 생기면 추적을 하는 파일

- 변화가 생겨도 추적을 하지 않는 파일

  - 개발자 또는 누군가가 파일을 건드리지 않아도 시스템상 자동으로 생성되거나 변경되는 파일, 하지만 프로젝트에 영향을 미치지 않는 파일

    **gitignore로 관리**

    - 변화가 생겨도 추적되지 않고 git의 add와 commit과정에 관여하지 않는다.

------

## 파일 추적 상태

![images_danna-lee_post_205b4922-a16c-421c-86f5-4764ecef6603_Slide6](https://user-images.githubusercontent.com/103401813/179659847-61685d37-1a57-42ca-8c0d-e131a048434f.png)

추적되는 파일

1. 변경없음 (unmodified)
   - 변경되지 않은 파일
2. 변경함 (modifed)
   - 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않은 것을 의미
3. 스테이지됨 (staged)
   - 현재 수정한 파일을 곧 커밋할 것이라고 표시한 상태를 의미
   - 파일을 수정(modifed)하고 staging area에 추가(git add)하면 staged상태라고 한다.

------

## add, commit : 체크포인트

git은 버전관리 시스템이다.

따라서 파일에 변동시 복구가 쉽고 변동 내역을 알아보기 쉽게 체크포인트를 찍어주는 것이 중요하다.

- 변경이 된 상태에서 체크포인트를 만드는 일을 **커밋한다(commit)**라고 한다.

### commit

![images_danna-lee_post_453dab30-2c89-423a-b395-9ab2e807e6bc_Slide7](https://user-images.githubusercontent.com/103401813/179659877-1610c36a-d56e-4765-a214-ec1164861bad.png)

깃크라겐

- Unstaged Files가 변경된 모든 파일
- Staged Files가 staged된 파일
- Stage all changes 버튼을 통해 변경된 모든 파일을 add 가능
- 마우스를 갖다대 Stage File 버튼을 눌러 개별 파일만 add 가능

주로 기능단위로 한다.

이유는 코드리뷰시 보기 간편하기 때문이다.

- ex) 컴포넌트 구성, 스타일 적용, 기능 함수 구현등으로 나눠서 commit

만약 한 번에 일을 처리 해버렸다면

**staged단계**를통해 해결할 수 있다.

- staged 단계 : commit을 위한 단계이다, modified 된 파일 중 선택적으로 파일을 stage해서 해당 내용만 commit 할 수 있게 한다.

Staged Files를 commit하기 위해 하단에 커밋 메시지를 적고 Commit changes to [n] files 버튼을 누르면 커밋이 완료 된다.

- 커밋 규칙을 정해놓는 것을 권장한다.
- ex)
  - Feat - 새로운 기능 추가
  - Fix - 버그 수정
  - Build - 빌드 관련 파일 수정
  - Ci - CI관련 설정 수정
  - Docs - 문서 (문서 추가, 수정, 삭제)
  - Style - 스타일 (코드 형식, 세미콜론 추가: 비즈니스 로직에 변경 없는 경우)
  - Refactor - 코드 리팩토링
  - Test - 테스트 (테스트 코드 추가, 수정, 삭제: 비즈니스 로직에 변경 없는 경우)
  - Chore - 기타 변경사항 (빌드 스크립트 수정 등)

만약 staged된 파일을 취소할 경우 Unstage all changes버튼 또는 파일 이름 위에 마우스를 올려 Unstage File 버튼을 누르면 add하기 전의 상태로 돌아간다.

## add 더 자세히 알아보기

![images_danna-lee_post_1db05ceb-aafc-4bea-898e-92482adabedf_Slide8](https://user-images.githubusercontent.com/103401813/179659921-ddcabaff-ca99-4b4c-9976-c3b44f30398a.png)

깃크라겐에서 add는

우측 패널에서 파일 이름을 눌러 파일 변경 내용에서 stage hunk를 누르면 파일 전체가 아닌 해당 부분만 stage가 가능하다.

- 기능 1, 기능 2를 커밋하는 등 한 파일 내에서 커밋을 쪼갤 때 주로 사용

라인 별로 stage를 관리할 수 있다. 코드 맨 왼쪽에 마우스를 가져다 대 +버튼을 누르면 줄 별로 따로 stage 가능하다.

------

## 작업 내용 없애기

![images_danna-lee_post_e0b21b11-cced-4bf5-9ec9-0f8f62b3d321_제목을-입력해주세요](https://user-images.githubusercontent.com/103401813/179659948-c1e6a5a1-7a30-4546-b2c7-563d293ed575.png)

마지막  커밋으로 가는 방법은 우측 패널에 휴지통 아이콘을 누르면 된다.

특정 내용만 날리고 싶다면 파일 이름을 누르고 들어가 Discard Hunk버튼을 눌러주면 해당 부분만 삭제된다.

------

## push, pull

commit을 하면 커밋 내역은 내 컴퓨터에만 저장되어 있는 상태이다. 협업 시에 다른 컴퓨터로 옮겨 현재 하고 있던 작업을 이어서 하기 위에 리모트에 업로드가 되어 있어야 한다.

- 리모트 : 인터넷이나 네트워크 어딘가에 있는 저장소
  - git remote : 프로젝트의 리모트 저장소를 관리하는 명령어 새로운 저장소를 추가하거나 변경가능

리모트하는 작업을 PUSH라고 한다.

리모트에 있는 내용을 로컬로 동기화 하는 걸 pull이라고 한다.

- 로컬 : 특정지역

pull = fetch(가져오기) + merge(병합하기)

------

## 브렌치 관리

협업 시 브렌치를 관리해야 한다.

![images_danna-lee_post_9248f0f3-d0c7-4217-a80d-1bce90697c8d_Slide10](https://user-images.githubusercontent.com/103401813/179660477-a901ae1f-705d-4d3e-8b7c-a3721df55f8b.png)

브렌치는 소프트웨어를 하나 개발할 시 여러 사람이 함께 개발을 시작할 때 작업 폴더 하나에서 동시에 작업을 한다면 다양한 문제가 발생한다.

- ex) 노션 동시 편집, docs편집

브랜치는 개발자들이 동시에 작업을 하지만 서로에게 전혀 영향을 주지 않도록 해주는 기능을 담당한다.

각자 독립적인 영역을 가지고 작업을 한 후에 작업이 끝나면 합칠 수 있다.

브랜치 생성 후 다른 브랜치의 파일이나 작업 내용은 전혀 보이지 않는다. 하지만 브랜치를 합치면 원래 브랜치와 합쳐진 브랜치의 두 내용이 모두 보이게 된다.

- 보통 브랜치는 기능 단위로 만드는 경우가 일반적이다.

## 브랜치 만드는 법

![images_danna-lee_post_19dc74f3-030a-4085-b179-9a3b48ec17cd_Slide11](https://user-images.githubusercontent.com/103401813/179660518-a6dbbaad-21c5-4c1f-9567-ab29fd3148ce.png)
