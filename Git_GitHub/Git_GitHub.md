# Git / GitHub

- Git이란?
    - **분산 버전 관리 시스템**으로 **코드의 버전을 관리**하는 도구이다.
    - 원격 저장소(Remote Repository)를 통해 여러 사용자들과 협업할 수 있다.

- Git 기본 명령어
    
    **$ git init**
    
    특정 폴더를 git 저장소(repository)로 만든다.
    자동으로 .git 폴더가 생성되며 git bash에서는 (master) 또는 (main) 이라고 표시된다.
    
    **$ git add <파일명.확장자>**
    
    작업(수정)한 파일이 Working directory에서 Staging area에 모은다.
    untracked / modified 상태의 파일을 staged 상태로 변경한다.
    
    * **$ git add . 명령어는 현재 디렉토리의 모든 파일을 add 한다.**
    
    **$ git commit -m ‘커밋메시지’**
    
    staged 상태의 파일을 커밋을 통해 버전으로 기록한다.
    커밋 메시지는 변경사항을 나타낼 수 있도록 명확하게 작성한다.
    
    **$ git log**
    
    현재 저장소의 커밋 기록을 조회한다.
    

- Git 사용자 설정 방법
    
    **$ git config –global user.name “username”
    $ git config –global user.email “my@email.com”**
    
    사용자 설정 명령어
    
    **$ git config -l
    $ git config –global-l
    $ git config user.name**
    
    사용자 설정 확인 명령어
    

- GitHub 원격 저장소 활용법
    1. GitHub에 New Repository를 생성한다.
    2. 생성한 저장소의 URL을 확인한다.
    3. 로컬 저장소에 원격 저장소의 정보를 설정한다.
        
        **$ git remote add origin <원격 저장소 URL>**
        
        * 일반적으로 원격 저장소에는 origin이라는 이름을 붙인다.
        
    4. 작업 후에는 변경사항(커밋)을 원격 저장소로 보낸다.
        
        **$ git push <원격저장소> <브랜치>
        $ git push origin master**
        
    
    5-1. 원격 저장소에서 변경된 파일 및 내역을 받아올 수도 있다.
    
    **$ git pull <원격저장소> <브랜치>
    $ git pull origin master**
    
    5-2. 다른 사용자의 원격 저장소를 복제하여 가져올 수 있다.
    
    **$ git clone <원격저장소 URL>**
    
    * GitHub 사이트 상에서 원격 저장소의 파일을 다운로드 받는 것도 가능하지만 파일을 다운로드할 경우 파일만 가져올 뿐 그 이전의 버전 기록까지 가져올 수는 없다.
    * clone은 원격 저장소 자체를 복제하는 것이고 pull은 원격 저장소의 커밋, 즉 변경된 파일만 가져온다.
    

- GitHub 활용하여 협업하기
    - 다른 사람과 협업하여 작업할 때 독립적인 작업 흐름을 만들어 관리하기 위해서는 branch를 활용한다.
    - 브랜치 주요 명령어
        
        **(master) $ git branch <브랜치명>**
        
        입력한 이름의 브랜치를 생성한다.
        
        **(master) $ git checkout <브랜치명>**
        
        입력한 이름의 브랜치로 이동한다.
        
        **(master) $ git checkout -b <브랜치명>**
        
        입력한 이름의 브랜치를 생성하고 이동한다.
        
        **(master) $ git branch -d <브랜치명>**
        
        입력한 이름의 브랜치를 삭제한다.
        
        **(master) $ git merge <브랜치명>**
        
        입력한 이름의 브랜치를 병합한다.
        
        * 서로 다른 커밋을 병합(merge)하는 과정에서 **같은 파일의 동일한 부분이 수정**되어 있는 경우, git이 auto merging을 하지 못하고 충돌 메시지가 뜬다. 충돌하는 부분이 해당 파일의 위치에 표준형식에 따라 표시되므로 원하는 형태의 코드로 수정한 후 직접 commit을 발생시킨다.
        
    - 협업 방식
        1. Shared Repository Model
            1. 동일한 저장소를 공유하여 활용하는 방식이다.
            2. 팀원을 collaborator로 등록하고 초대하여 동일한 저장소를 clone하여 작업한다.
            3. 브랜치에서 작업하고 GitHub으로 Push한다.
            4. 작업자는 작업 후 GitHub에서 Pull Request를 생성하고 관리자는 작성된 코드를 확인한 후 병합한다.
        2. Fork & Pull Model
            1. 원격 저장소를 fork한 후 내 저장소로 복제본을 가져온 뒤 로컬에서 작업 후 원격 저장소로 push하는 방식이다.
            2. Repository에 collaborator로 등록되지 않은 상태에서도 가능하다.
            3. GitHub 기반의 오픈소스 참여 과정에서 쓰인다.