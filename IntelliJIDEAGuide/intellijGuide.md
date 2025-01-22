# 📓인텔리제이 가이드

---
<details>
    <summary><h3>코드 Edit</h3></summary>

**메인메서드 생성 및 실행**
* 디렉토리, 패키지, 클래스 등 생성 목록 보기
  * 맥 - Command(⌘) + N
  * 윈도우, 리눅스 - Alt + Insert
* 코드 템플릿
  * 메인 메서드 - psvm(public static void main(String[] args))
  * 표준 출력 - sout(System.out.println())
* 실행환경 실행
  * 현재 포커스
    * 맥 - Ctrl(⌃) + Shift(⇧) + R
    * 윈도우, 리눅스 - Ctrl + Shift + F10
  * 이전 실행
    * 맥 - Ctrl(⌃) + R
    * 윈도우, 리눅스 - Shift + F10

**라인 수정하기**
* 라인 복사하기
  * 맥 - Command(⌘) + D
  * 윈도우, 리눅스 - Ctrl + D
* 라인 삭제하기
  * 맥 - Command(⌘) + Backspace(⌫)
  * 윈도우, 리눅스 - Ctrl + Y
* 라인 합치기
  * 맥 - Ctrl(⌃) + Shift(⇧) + J
  * 윈도우, 리눅스 - Ctrl + Shift + J
* 라인 단위로 옮기기
  * 구문 이동
    * 맥 - Command(⌘) + Shift(⇧) + ↑↓
    * 윈도우, 리눅스 - Ctrl + Shift + ↑↓
  * 라인 이동
    * 맥 - Option(⌥) + Shift(⇧) + ↑↓
    * 윈도우, 리눅스 - Alt + Shift + ↑↓
* Element 단위로 옮기기
  * 맥 - Command(⌘) + Shift(⇧) + Option(⌥) + ⮂
  * 윈도우, 리눅스 - Ctrl + Alt + Shift + ⮂

**코드 즉시보기**
* 인자값 즉시 보기
  * 맥 - Command(⌘) + P
  * 윈도우, 리눅스 - Ctrl + P
* 코드 구현부 즉시 보기
  * 맥 - Option(⌥) + Space(⎵)
  * 윈도우, 리눅스 - Ctrl + Shift + I
* Doc 즉시 보기
  * 맥 - F1
  * 윈도우, 리눅스 - Ctrl + Q

</details>

---

<details>
  <summary><h3>포커스</h3></summary>

**포커스 에디터**
* 단어별 이동
  * 맥 - Alt + ⮂
  * 윈도우, 리눅스 - Ctrl + ⮂
* 단어별 선택
  * 맥 - Alt + Shift + ⮂
  * 윈도우, 리눅스 - Ctrl + Shift + ⮂
* 라인 첫/끝 이동
  * 맥 - Fn + ⮂
  * 윈도우, 리눅스 - Home/End
* 라인 전체 선택
  * 맥 - Command + Shift + ⮂
  * 윈도우, 리눅스 - Shift + Home/End
* Page Up/Down
  * 맥 - Fn + ↑↓
  * 윈도우, 리눅스 - Page Up/Page Down

**포커스 특수키**
* 포커스 범위 한 단계씩 늘리기
  * 맥 - Alt + ↑↓
  * 윈도우, 리눅스 - Ctrl + W (확장) / Shift + Ctrl + W (축소)
* 포커스 뒤로/앞으로 가기
  * 맥 - Command + [ / ]
  * 윈도우, 리눅스 - Ctrl + Alt + ⮂
* 멀티 포커스
  * 맥 - Alt + Alt + ↓
  * 윈도우, 리눅스 - Ctrl + Ctrl + ↓
* 오류 라인 자동 포커스
  * 맥 - F2
  * 윈도우, 리눅스 - F2
</details>

---

<details>
  <summary><h3>검색</h3></summary>

**검색 텍스트**
* 현재 파일에서 검색
  * 맥 - Command + F
  * 윈도우, 리눅스 - Ctrl + F
* 현재 파일에서 교체
  * 맥 - Command + R
  * 윈도우, 리눅스 - Ctrl + R
* 전체에서 검색
  * 맥 - Command + Shift + F
  * 윈도우, 리눅스 - Ctrl + Shift + F
* 전체에서 교체
  * 맥 - Command + Shift + R
  * 윈도우, 리눅스 - Ctrl + Shift + R
* 정규표현식으로 검색, 교체
  * 맥 - Regex 체크
  * 윈도우, 리눅스 - Regex 체크

**검색 기타**
* 파일 검색
  * 맥 - Command + Shift + O
  * 윈도우, 리눅스 - Ctrl + Shift + N
* 메서드 검색
  * 맥 - Command + Alt + O
  * 윈도우, 리눅스 - Ctrl + Shift + Alt + N
* Action 검색
  * 맥 - Command + Shift + A
  * 윈도우, 리눅스 - Ctrl + Shift + A
* 최근 열었던 파일 목록 보기
  * 맥 - Command + E
  * 윈도우, 리눅스 - Ctrl + E
* 최근 수정했던 파일 목록 보기
  * 맥 - Command + Shift + E
  * 윈도우, 리눅스 - Ctrl + Shift + E
</details>

---

<details>
  <summary><h3>자동완성</h3></summary>

**자동완성**
* 스마트 자동 완성
  * 맥 - Ctrl + Shift + Space
  * 윈도우, 리눅스 - Ctrl + Shift + Space
* 스태틱 메서드 자동 완성
  * 맥 - Ctrl + Space x 2(2번)
  * 윈도우, 리눅스 - Ctrl + Space x 2(2번)
* Getter/Setter/생성자 자동완성
  * 맥 - Command + N
  * 윈도우, 리눅스 - Alt + Insert
* Override 메서드 자동완성
  * 맥 - Ctrl + I
  * 윈도우, 리눅스 - Ctrl + I

**Live Template**
* Live Template 목록 보기
  * 맥 - Command + J
  * 윈도우, 리눅스 - Ctrl + J
</details>

---

<details>
  <summary><h3>리팩토링</h3></summary>

**리팩토링 Extract**
* 변수 추출하기
  * 맥 - Command + Option + V
  * 윈도우, 리눅스 - Ctrl + Alt + V
* 파라미터 추출하기
  * 맥 - Command + Option + P
  * 윈도우, 리눅스 - Ctrl + Alt + P
* 메서드 추출하기
  * 맥 - Command + Option + M
  * 윈도우, 리눅스 - Command + Alt + M
* 이너 클래스 추출하기
  * 맥 - F6
  * 윈도우, 리눅스 - F6

**리팩토링 기타**
* 이름 일괄 변경하기
  * 맥 - Shift + F6
  * 윈도우, 리눅스 - Shift + F6
* 타입 일괄 변경하기
  * 맥 - Command + Shift + F6
  * 윈도우, 리눅스 - Ctrl + Shift + F6
* Import 정리하기
  * 맥 - Ctrl + Option + O
  * 윈도우, 리눅스 - Ctrl + Alt + O
  * Import 자동 정리하기
    * optimize import on the fly -> On 으로 설정
* 코드 자동 정렬하기
  * 맥 - Command + Option + L
  * 윈도우, 리눅스 - Ctrl + Alt + L
</details>

---

<details>
  <summary><h3>디버깅</h3></summary>

**디버깅**
* Debug 모드로 실행하기(현재위치의 메서드)
  * 맥 - Ctrl + Shift + D
  * 윈도우, 리눅스 - 없음
* Debug 모드로 실행하기(이전에 실행한 메서드)
  * 맥 - Ctrl + D
  * 윈도우, 리눅스 - Shift + F9
* Resume(다음 브레이크 포인트로 이동)
  * 맥 - Command + Option + R
  * 윈도우, 리눅스 - F9
* Step Over(현재 브레이크에서 다음 한줄로 이동)
  * 맥 - F8
  * 윈도우, 리눅스 - F8
* Step Into(현재 브레이크에서 다음 메서드로 이동)
  * 맥 - F7
  * 윈도우, 리눅스 - F7
* Step Out(현재 메서드의 밖으로 이동)
  * 맥 - Shift + F8
  * 윈도우, 리눅스 - Shift + F8
* Evaluate Expression(브레이크된 상태에서 코드 사용하기)
  * 맥 - Option + F8
  * 윈도우, 리눅스 - Alt + F8
* Watch(브레이크 이후의 코드 변경 확인하기)
  * 맥 - 없음
  * 윈도우, 리눅스 - 없음
</details>

---

<details>
  <summary><h3>Git&Github</h3></summary>

**Git 기본 기능 사용하기**
* Git View On
  * 맥 - Command + 9
  * 윈도우, 리눅스 - Alt + 9
* Git Option Popup
  * 맥 - Ctrl + V
  * 윈도우, 리눅스 - Alt + `(Back Quote)
* Commit
  * 맥 - Command + K
  * 윈도우, 리눅스 - Ctrl + K
* Push
  * 맥 - Command + Shift + K
  * 윈도우, 리눅스 - Ctrl + Shift + K
* Pull
  * 맥 - Command + Shift + A => git pull
  * 윈도우, 리눅스 - Ctrl + Shift + A => git pull

**Github 연동하기**
* Github 연동하기
  * 맥 - Command + Shift + A => share github
  * 윈도우, 리눅스 - Ctrl + Shift + A => share github
* Github Clone
  * IntelliJ 메인 화면 -> Checkout from Version Control -> 연동할 git url 입력
</details>
