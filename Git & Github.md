# Git & Github
## 2021-01-17 (일)
---
## 코코아톡 클론 코딩 (#5)
### 특징
- Git은 파일들을 주시하면서 관리해주는 도구이고, Github는 Git의 변경내역을 볼 수 있는 사이트이다.
- 코드가 많은 파일을 관리할 때, 파일의 히스토리를 알고싶을때(버전관리) 효과적
- txt, img, js 등 어떤 파일이든 업로드 및 변경내역을 확인가능
- 깃 시스템은 파일을 바이너리 포맷으로 인식한다. 
- 컴퓨터가 고장나거나 잃어버릴 경우를 대비하여 github를 이용한다.
- 깃은 파일을 계속 추적하고, 깃허브에 변경내역을 업로드하여 관리한다.
- [git-scm.com](git-scm.com)에서 OS에 맞는 Git 다운로드 가능

### 사용 방법
- github 계정 생성 및 로그인 후
- github의 repository에서 파일을 클릭하고 오른쪽 위의 history를 클릭하면 파일의 변경내역을 확인 가능하다.
  - repository : 코드를 넣는 폴더 (history가 저장됨)
  - commit : 저장 시점
  - 변경된 코드 확인가능, -는 제거, +는 추가

- repsitory 생성에는 두가지의 방법이 있다.
  1. 컴퓨터에 폴더 생성 후 github에 업로드
  2. 처음부터 github에 repository 생성 (추천)
     1.  owner 및 repository name 설정
     2. 설명 작성 (선택)
     3. public(공개) / private(비공개) : 감추어야하는 정보가 아니라면 public을 선택한다.
     4. 나머지는 설정하지 않고 처음대로 둠
     5. create repository 클릭
     6. github desktop 다운로드 및 설치
     7. 실행 및 로그인(github의 계정)
     8. clone a repository 선택 후 폴더의 저장경로 설정 (찾기 쉬운 경로로의 설정을 추천)
     9. clone 클릭


- 사용방법 (VSCode) 
  1. vscode에 생성한 폴더를 드래그 앤 드랍
  2. readme는 md(markdown)파일로 작성
  3. githubdesktop에 추가된 코드나 파일 확인가능
  4. 파일 체크박스 선택 후 summary작성 후 commit to master 클릭
  5. 위쪽의 publish branch 클릭
  6. github에서 확인가능
  7. 파일의 수정은 summary를 작성하지 않아도 가능
  8. commit은 컴퓨터에서 업로드 준비가 완료됐다는 것, push를 클릭해주어야 github에 업로드
