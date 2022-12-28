# Git

## Git이란?
- Git은 `분산버전관리시스템`으로 `코드의 버전을 관리`하는 도구이다.
- 2005년 리눅스 커널을 위한 도구로 리누스 토르발스가 개발하였다.
- 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율 가능하다.
- 데이터를 파일 시스템의 스냅샷으로 관리하고 매우 크기가 작다.
- 파일이 달리지지 않으면 성능을 위해 파일을 새로 저장하지 않는다.

## 분산버전관리시스템(DVCS)
- 중앙집중식버전관리시스템은 중앙에서 버전을 관리하고 파일을 받아서 사용한다.
- 반면에 분산버전관리시스템은 원격 저장소(remote repository)를 통하여 협업하고, 모든 히스토리를 클라이언트들이 공유한다.

## Git 기본 흐름
1. 작업(수정)한 파일은 Working directory에 위치한다.
    - untracked / modified -> staged
2. 1번의 파일을 add하여 Staging area에 모은다.
    - staged -> committed
3. 모인 파일을 commit하여 버전으로 기록한다.

## 기본 명령어
- $ git init
  - 특정 폴더를 git 저장소(repository)를 만들어 git으로 관리
    - .git 폴더가 생성됨
    - git bash에서는 (master) 또는 (main) 이라는 표기를 확인할 수 있음
- $ git add 파일명.확장자
  - working directory상의 변경 내용을 staging area에 추가하기 위해 사용
    - untracked 상태의 파일을 staged로 변경
    - modified 상태의 파일을 staged로 변경
  - git add . 은 현재 디렉토리의 모든 파일을 add 
- $ git commit -m '커밋메시지'
  - staged 상태의 파일들을 커밋을 통해 버전으로 기록
  - SHA-1 해시를 사용하여 40자 길이의 체크섬을 생성하고, 이를 통해 고유한 커밋을 표기
  - 커밋 메시지는 변경사항을 나타낼 수 있도록 명확하게 작성해야 함
- $ git status
  - git 저장소에 있는 파일의 상태를 확인하기 위하여 활용
    - Untracked: 버전으로 관리된 적 없는 파일(새로 만든 경우)
    - Tracked: 이전부터 버전으로 관리되고 있는 파일
      - Unmodified: 수정되지 않은 파일, git status에 나타나지 않음
      - Modified: Changes not staged for commit(수정되었으나 staged 되지 않은 파일)
      - Staged: Changes to be committed(staged 되었으나 commit 되지 않은 파일)
    - Nothing to commit, working tree clean: 작업(수정)한 파일이 모두 커밋된 상태이고 별도의 수정사항 또한 없는 상태
- $ git log
  - 현재 저장소에 기록된 커밋을 조회
  - 다양한 옵션을 통해 로그를 조회할 수 있음
    - $ git log -1
    - $ git log --online
    - $ git log -2 --online

## Git 설정 파일(config)
- 사용자 정보(commit author): 커밋을 하기 위해 반드시 필요
  - git config --global user.name "username"
  - git config --global user.email "my@email.com"
- 설정 확인
  - git config -l
  - git config --global-l
  - git config user.name

## GitHub 원격저장소 활용하는 방법
1. GitHub에서 New Repository 생성
2. 원격저장소의 URL을 확인
    - 예시: https://github.com/Rilee-0320/TIL.git
3. 로컬 저장소에 원격 저장소 정보 설정하기
    - \$ git remote add orgin <원격저장소 URL>
4. 로컬 저장소의 버전을 원격 저장소로 보내기
    - 원격저장소로 로컬 저장소의 변경사항(커밋)을 올림(push)
    - \$ git push <원격저장소> <브랜치>
    - \$ git push origin master
5. 원격저장소로부터 변경된 내역을 받아오기
    - \$ git pull <원격저장소> <브랜치>
    - \$ git pull origin master
6. 원격저장소 프로젝트 시작하기
    - $ git clone <원격저장소 url> : 원격저장소를 복제하여 가져옴
    - cf. 원격저장소의 파일을 다운로드받는 것은 최신 commit, push 된 파일만 가져올 뿐 그 이전의 버전 기록까지 가져오지 않음
    - cf. clone은 원격저장소를 복제하는 것이나 pull은 원격저장소의 커밋만을 가져옴

### 기타 명령어
- git remote -v : 원격저장소 정보 확인
- git remote rm <원격저장소> : 원격저장소 삭제
- git pull <원격저장소> <브랜치> : 원격저장소로부터 pull

## .gitignore
- 개발 프로젝트에서 별도로 버전 관리를 하지 않아야 할, 즉 커밋하지 않을 파일, 디렉토리가 발생함
- .gitignore 파일을 생성하고 해당 파일명 또는 디렉토리명을 입력할 경우 해당 파일, 디렉토리를 제외하고 커밋 가능
- 참고: [.gitignore.io](https://www.toptal.com/developers/gitignore/)

## Git 관련 참고자료
- [누구나 쉽게 이해할 수 있는 Git](https://backlog.com/git-tutorial/kr/)
- [Pro Git](https://git-scm.com/book/ko/v2)
