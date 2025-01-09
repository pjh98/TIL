# 📖팀 개발을 위한 Git·Github 시작하기
> 책을 읽고 실습 진행하면서 배운 내용들 정리

## 1. Git과 GitHub

### Git

- 소스코드 버전 관리 시스템으로, 데이터를 저장할 공간만 있다면 어디서나 사용 가능.
- 개인 컴퓨터에만 저장하면 나 혼자 사용 가능, 구글 드라이브나 드롭박스 같은 클라우드 서버에 올려두면
팀 프로젝트를 하는 팀원과 함께 인터넷을 통해 버전 관리 가능.

### GitHub

- Git으로 관리하는 프로젝트를 올려둘 수 있는 Git 호스팅 사이트 중 하나


## 2. Git을 설치하고 로컬저장소에서 커밋 관리하기
>Git Bash는 리눅스 기반의 터미널로 윈도우에서도 git을 다운받으면 사용 가능

### 1. Git Bash 창에서 '$' 기호 뒤에 명령어를 입력하여 사용

**앞으로 나오는 코드는 모두 샘플**

- pjh@DESKTOP - 3HONHJE MINGW64~  
$ `git init`

> 버전 관리를 위한 내 정보 등록  
> GitHub에 등록된 Email, Username을 입력
- $ `git config --global user.email "hello.git.GitHub@gmail.com`
- $ `git config --global user.name "Cat-Hanbit`

> 커밋에 추가할 파일 선택  
- $ `git add README.md`

> 커밋에 대한 상세 설명  
- $ `git commit -m "사이트 설명 추가"`

> 지금까지 만든 커밋 확인
- $ `git log`

> 원하는 커밋으로 코드 되돌리기
- $ `git checkout 96a3ee5(원하는 커밋의 앞 7자리 아이디)`
- $ `git checkout -` (최신 커밋으로 되돌리기)

> 원격저장소에 커밋 올리기
- $ `git remote add origin https://GitHub.com/pjh/gitTest.git`
- $ `git push origin master`

> 원격저장소 커밋을 로컬저장소에 내려받기
- $ `git clone https://GitHub.com/pjh/gitTest .`
- $ `git pull origin master`
