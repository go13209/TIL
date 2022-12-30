# :star: Git

## :bulb: Git이란?
- Git은 `분산버전관리시스템`으로 `코드의 버전을 관리`하는 도구이다.
- 2005년 리눅스 커널을 위한 도구로 리누스 토르발스가 개발하였다.
- 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율 가능하다.
- 데이터를 파일 시스템의 스냅샷으로 관리하고 매우 크기가 작다.
- 파일이 달라지지 않으면 성능을 위해 파일을 새로 저장하지 않는다.

## :bulb: 분산버전관리시스템(DVCS)
- 중앙집중식버전관리시스템은 중앙에서 버전을 관리하고 파일을 받아서 사용한다.
- 반면에 분산버전관리시스템은 원격 저장소(remote repository)를 통하여 협업하고, 모든 히스토리를 클라이언트들이 공유한다.

## :bulb: Git 기본 흐름
1. 작업(수정)한 파일은 Working directory에 위치한다.
2. 1번의 파일을 add하여 Staging area에 모은다.
    - untracked / modified -> staged
3. 모인 파일을 commit하여 버전으로 기록한다.
    - staged -> committed

## :bulb: Git 기본 명령어
- $ git init
  - 특정 폴더를 git 저장소(repository)로 만들어 git으로 관리
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

## :bulb: Git 설정 파일(config)
- 사용자 정보(commit author): 커밋을 하기 위해 반드시 필요
  - git config --global user.name "username"
  - git config --global user.email "my@email.com"
- 설정 확인
  - git config -l
  - git config --global-l
  - git config user.name

## :bulb: GitHub 원격저장소 활용하는 방법
1. GitHub에서 New Repository 생성
2. 원격저장소의 URL을 확인
    - 예시: https://github.com/Rilee-0320/TIL.git
3. 로컬 저장소에 원격 저장소 정보 설정하기
    - \$ git remote add orgin <원격저장소 URL>
    - 일반적으로 원격저장소에는 origin이라는 이름을 붙임
4. 로컬 저장소의 버전을 원격 저장소로 보내기
    - 원격저장소로 로컬 저장소의 변경사항(커밋)을 올림(push)
    - \$ git push <원격저장소> <브랜치>
    - \$ git push origin master
5. 원격저장소로부터 변경된 내역을 받아오기
    - \$ git pull <원격저장소> <브랜치>
    - \$ git pull origin master
6. 원격저장소 프로젝트 시작하기
    - $ git clone <원격저장소 url> : 원격저장소를 복제하여 가져옴
    - cf. 원격저장소의 파일을 다운로드 받는 것은 최신 commit, push 된 파일만 가져올 뿐 그 이전의 버전 기록까지 가져오지 않음
    - cf. clone은 원격저장소를 복제하는 것이나 pull은 원격저장소의 커밋만을 가져옴

### 기타 명령어
- git remote -v : 원격저장소 정보 확인
- git remote rm <원격저장소> : 원격저장소 삭제

## :bulb: .gitignore
- 개발 프로젝트에서 별도로 버전 관리를 하지 말아야 할, 즉 커밋하지 않을 파일, 디렉토리가 발생함
- .gitignore 파일을 생성하고 해당 파일명 또는 디렉토리명을 입력할 경우 해당 파일, 디렉토리를 제외하고 커밋 가능
- 참고: [.gitignore.io](https://www.toptal.com/developers/gitignore/)

## :bulb: Git branch
- 독립적인 작업흐름을 만들고 관리하기 위해 branch 활용
- 브랜치 주요 명령어
  - (master) $ git branch {브랜치명} : 브랜치 생성
  - (master) $ git checkout {브랜치명} : 브랜치 이동
  - (master) $ git checkout -b {브랜치명} : 브랜치 생성 및 이동
  - (master) $ git branch : 브랜치 목록
  - (master) $ git branch -d {브랜치명} : 브랜치 삭제
  - (master) $ git merge {브랜치명} : 브랜치 병합

  ### Git branch 병합
  1. fast-foward : 브랜치 생성된 이후 master 브랜치에 변경 사항이 없는 상황
      - 예시
      1. {feature/home} branch 생성 및 이동
        ```bash
        (master) $ git branch feature/home
        (master) $ git checkout feature/home
        ```
      2. 작업 완료 후 commit
        ```bash
        (feature/home) $ touch home.txt
        (feature/home) $ git add .
        (feature/home) $ git commit -m 'Add home.txt'
        (feature/home) $ git log --oneline
        b534a34 (HEAD -> feature/home) Complete Home!!!!
        e89616a (master) Init
        ```
      3. master 이동
        ```bash
        (feature/home) $ git checkout master
        (master) $ git log --oneline
        ```
      4. master에 병합
        ```bash
        (master) $ git merge feature/home 
        Updating e89616a..b534a34
        Fast-forward
          home.txt | 0
          1 file changed, 0 insertions(+), 0 deletions(-)
          create mode 100644 home.txt
        ```
      5. 결과 : fast-foward
        ```bash
        (master) $ git log --oneline
        b534a34 (HEAD -> master, feature/home) Complete Home!!!!
        e89616a Init
        ```
      6. branch 삭제
        ```bash
        (master) $ git branch -d feature/home 
        Deleted branch feature/home (was b534a34).
        ```
  2. merge commit : 서로 다른 이력(commit)을 병합(merge)하는 과정에서 **다른 파일이 수정**되어 있는 상황, git이 auto merging을 진행하고, **commit이 발생**
      - 예시
      1. {feature/about} branch 생성 및 이동
        ```bash
        (master) $ git checkout -b feature/about
        (feature/about) $
        ```
      2. 작업 완료 후 commit
        ```bash
        (feature/about) $ touch about.txt
        (feature/about) $ git add .
        (feature/about) $ git commit -m 'Add about.txt'
        (feature/about) $ git log --oneline
        5e1f6de (HEAD -> feature/about) 자기소개 페이지 완료!
        b534a34 (master) Complete Home!!!!
        e89616a Init
        ```
      3. master 이동
        ```bash
        (feature/about) $ git checkout master
        (master) $
        ```
      4. *master에 추가 commit 발생시키기!!*
        * **다른 파일을 수정 혹은 생성하자!**
        ```bash
        (master) $ touch master.txt
        (master) $ git add .
        (master) $ git commit -m 'Add master.txt'
        (master) $ git log --oneline
        98c5528 (HEAD -> master) 마스터 작업....
        b534a34 Complete Home!!!!
        e89616a Init
        ```
      5. master에 병합
        ```bash
        (master) $ git merge feature/about
        ```
      6. 결과 -> 자동으로 *merge commit 발생*
      7. 커밋 및 그래프 확인하기
        ```bash
        $ git log --oneline --graph
        *   582902d (HEAD -> master) Merge branch 'feature/about'
        |\
        | * 5e1f6de (feature/about) 자기소개 페이지 완료!
        * | 98c5528 마스터 작업....
        |/
        * b534a34 Complete Home!!!!
        * e89616a Init
        ```
      8. branch 삭제
        ```bash
        $ git branch -d feature/about 
        Deleted branch feature/about (was 5e1f6de).
        ```
  3. merge commit 충돌서로 다른 이력(commit)을 병합(merge)하는 과정에서 **같은 파일의 동일한 부분이 수정**되어 있는 상황, git이 auto merging을 하지 못하고 충돌 메시지가 뜸, 해당 파일의 위치에 표준형식에 따라 표시, 원하는 형태의 코드로 직접 수정을 하고 직접 commit을 발생 시켜야 함
      - 예시
      1. {feature/test} branch 생성 및 이동
        ```bash
        (master) $ git checkout -b feature/test
        ```
      2. 작업 완료 후 commit
        ```bash
        # README.md 파일 열어서 수정
        (feature/test) $ touch test.txt
        (feature/test) $ git add .
        (feature/test) $ git commit -m 'Add test.txt'
        (feature/test) $ git log --oneline
        95fad1c (HEAD -> feature/test) README 수정하고 test 작성하고
        582902d (master) Merge branch 'feature/about'
        98c5528 마스터 작업....
        5e1f6de 자기소개 페이지 완료!
        b534a34 Complete Home!!!!
        e89616a Init
        ```
      3. master 이동
        ```bash
        $ git checkout master
        ```
      4. *master에 추가 commit 발생시키기!!*
        * **동일 파일을 수정 혹은 생성하자!**
        ```bash
        # README.md 파일 열어서 수정
        (master) $ git add README.md
        (master) $ git commit -m 'Update README.md'
        ```
      5. master에 병합
        ```bash
        (master) $ git merge feature/test 
        Auto-merging README.md
        CONFLICT (content): Merge conflict in README.md
        Automatic merge failed; fix conflicts and then commit the result.
        ```
      6. 결과 -> *merge conflict발생*
        > git status 명령어로 충돌 파일을 확인할 수 있음
        ```bash
        (master|MERGING) $ git status
        On branch master
        You have unmerged paths.
          (fix conflicts and run "git commit")        
          (use "git merge --abort" to abort the merge)
        
        Changes to be committed:
                new file:   test-1.txt
                new file:   test-2.txt
                new file:   test.txt
        
        Unmerged paths:
          (use "git add <file>..." to mark resolution)
                both modified:   README.md
        ```
      7. 충돌 확인 및 해결

        ```
        <<<<<<< HEAD
        # 마스터에서 작업함...
        =======
        # 테스트에서 작성
        >>>>>>> feature/test
        ```
      8. merge commit 진행
        ```bash
        (master|MERGING) $ git add .
        (master|MERGING) $ git commit
        ```
        * vim 편집기 화면이 나타남
          * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력하여 저장 및 종료함
          * `w` : write
          * `q` : quit

        * vs code 편집기에서 메시지보고 닫아주자!
      9. 커밋 및 확인하기

        ```bash
        (master) $ git log --oneline --graph
        *   bc1c0cd (HEAD -> master) Merge branch 'feature/test'
        |\  
        | * 95fad1c (feature/test) README 수정하고 test 작성하고
        * | 2ecad28 리드미 수정
        |/  
        *   582902d Merge branch 'feature/about'
        |\  
        | * 5e1f6de 자기소개 페이지 완료!
        * | 98c5528 마스터 작업....
        |/  
        * b534a34 Complete Home!!!!
        * e89616a Init
        ```
      10. branch 삭제
        ```bash
        (master) $ git branch -d feature/test
        ```

## :bulb: Git Flow
- Git을 활용하여 협업하는 흐름으로 branch를 활용하는 전략
- 각자 독립된 버전의 흐름을 만들 수 있음

### GitHub Flow 기본 원칙
1. master branch는 반드시 배포 가능한 상태여야 한다.
2. feature branch는 각 기능의 의도를 알 수 있도록 작성한다.
3. commit message는 매우 중요하며, 명확하게 작성한다.
4. Pull Request를 통해 협업을 진행한다.
5. 변경 사항을 반영하고 싶다면 master branch에 병합한다.

### GitHub Flow Models
1. Shared Repository Model
  - 동일한 저장소를 공유하여 활용하는 방식
  - 팀원을 collaborator로 등록하고 초대하여 동일한 저장소를 clone 하여 작업
  - 브랜치에서 작업하고 GitHub으로 Push
    - 항상 독립적인 feature branch에서 작업
    - Commit으로 작업의 이력을 남김
    - 완성된 코드는 원격 저장소로 push 함
  - Pull Request 생성 및 Review, Merge
    - GitHub에서 Pull Request 버튼을 누르고 요청을 생성
    - 관리자는 작성된 코드를 확인 후 병합
2. Fork & Pull Model
  - Repository에 Collaborator로 등록되지 않은 상태에서 진행
  - GitHub 기반의 오픈소스 참여 과정에서 쓰이는 방식
  - 원격 저장소를 fork 한 후 내 저장소로 복제본을 가져온 뒤 로컬에서 작업 후 원격 저장소로 push 가능

## :bulb: Git 관련 참고자료
- [누구나 쉽게 이해할 수 있는 Git](https://backlog.com/git-tutorial/kr/)
- [Pro Git](https://git-scm.com/book/ko/v2)
- [좋은 git commit 메시지를 위한 영어 사전](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)
- [좋은 git 커밋 메시지를 작성하기 위한 7가지 약속](https://meetup.nhncloud.com/posts/106)