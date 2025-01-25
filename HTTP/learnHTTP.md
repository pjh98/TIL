# 📡모든 개발자를 위한 HTTP 웹 기본 지식

---

<details>
    <summary><h3>인터넷 네트워크</h3></summary>

**IP(Internet Protocol)**
* IP의 역할
  * 지정한 IP 주소(IP Address)에 데이터를 전달
  * 패킷(Packet)이라는 통신 단위로 데이터 전달
  * IP 패킷 정보 - 출발지 IP, 목적지 IP 등 
* IP의 한계
  * 비연결성
    * 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
  * 비신뢰성
    * 중간에 패킷이 사라지면?
    * 패킷이 순서대로 안오면?
  * 프로그램 구분
    * 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상이면?

**TCP,UDP**
* IP 스택의 4계층
  * 애플리케이션 계층 - HTTP, FTP
  * 전송 계층 - TCP, UDP
  * 인터넷 계층 - IP
  * 네트워크 인터페이스 계층
* TCP 패킷 정보 - 출발지 PORT, 목적지 PORT, 전송 제어, 순서, 검증 정보 등
* TCP(Transmission Control Protocol : 전송 제어 프로토콜) 특징
  * 연결지향 - TCP 3 way handshake(가상 연결)
    * SYN(Synchronize Sequence Number), SYN + ACK(Acknowledgment), ACK
  * 데이터 전달 보증
  * 순서 보장
  * 신뢰할 수 있는 프로토콜
  * 현재는 대부분 TCP 사용
* UDP(User Datagram Protocol : 사용자 데이터그램 프로토콜)
  * 하얀 도화지에 비유(기능이 거의 없음)
  * 연결지향 X
  * 데이터 전달 보증 X
  * 순서 보장 X
  * 데이터 전달 및 순서가 보장되지 않지만 단순하고 빠름
  * IP와 거의 같고 PORT, 체크섬 정도만 추가
  * 애플리케이션에서 추가 작업 필요

**PORT**
* 같은 IP 내에서 프로세스 구분
  * 0 ~ 65536 할당 가능
  * 0 ~ 1023 : 잘 알려진 포트, 사용하지 않는 것이 좋음
    * FTP - 20, 21
    * TELNET - 23
    * HTTP - 80
    * HTTPS - 443

**DNS(Domain Name System)**
* IP는 기억하기 어렵고 변경될 수 있음
* 도메인 명을 IP주소로 변환

</details>

---

<details>
    <summary><h3>URI와 웹 브라우저 요청 흐름</h3></summary>

**URI(Uniform Resource Identifier)**
* URI는 로케이터(locator), 이름(name) 또는 둘다 추가로 분류될 수 있다.

![Image](https://github.com/user-attachments/assets/be1e6e47-17f5-4b6f-a134-c2f70c14331f)

* URL - 리소스가 있는 위치를 지정
* URN - 리소스에 이름을 부여
* 위치는 변할 수 있지만 이름은 변하지 않는다.
* URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않음

**URL 문법**
>ex) <br> `https`://`www.google.com`:`443`/`search` `?q=hello&hl=ko` <br>
> `scheme`://[userinfo@]`host`[:`port`][/`path`][`?query`][#fragment]

* scheme `https`
  * 주로 프로토콜 사용
  * 프로토콜 - 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙(ex)http, https, ftp 등)
  * 포트는 생략 가능
* userinfo
  * URL에 사용자 정보를 포함해서 인증
  * 거의 사용하지 않음
* host `www.google.com`
  * 호스트명
  * 도메인명 또는 IP주소를 직접 사용가능
* port `443`
  * 접속 포트
  * 일반적으로 생략, 생략시 http는 80, https는 443
* path `search`
  * 리소스 경로, 계층적 구조
* query `?q=hello&hl=ko`
  * key = value 형태
  * ?로 시작, &로 추가 가능 ?keyA = valueA&keyB = valueB
  * query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터, 문자 형태
* fragment
  * html 내부 북마크 등에 사용
  * 서버에 전송하는 정보 아님

**웹 브라우저 요청 흐름**

![Image](https://github.com/user-attachments/assets/bfcf1075-6c50-4e4e-bda5-6c7ccdc71daa)
* HTTP 요청 메시지
  ```
  GET /search?q=hello&hl=ko HTTP/1.1
  Host: www.google.com
  ```
* HTTP 응답 메시지
  ```
  HTTP/1.1 200 OK
  Content-Type: text/html;charset=UTF-8
  Content-Length: 3423
    
  <html>
    <body>...</body>
  </html>
  ```
</details>

---

<details>
  <summary><h3>HTTP(HyperText Transfer Protocol)</h3></summary>

**모든것이 HTTP**
* HTTP메시지에 모든것을 전송
  * HTML, IMAGE, JSON, XML(API) 등 거의 모든 형태의 데이터 전송 가능
  * 서버간 데이터를 주고 받을 때도 대부분 HTTP 사용
* HTTP 역사
  * HTTP/0.9 1991년 - GET 메서드만 지원, HTTP 헤더 X
  * HTTP/1.0 1996년 - 메서드, 헤더 추가
  * HTTP/1.1 1997년 - 가장 많이 사용, 가장 중요한 버전
    * RFC2068(1997) -> RFC2616(1999) -> RFC7230~7235(2014)
  * HTTP/2 2015년 - 성능 개선
  * HTTP/3 진행중 - TCP 대신 UDP 사용, 성능 개선
* HTTP 특징
  * 클라이언트 서버 구조
  * 무상태 프로토콜(Stateless), 비연결성
  * HTTP 메시지
  * 단순함, 확장 가능

**클라이언트 서버 구조**
* Request Response 구조
* 클라이언트는 서버에 요청을 보내고 응답 대기
* 서버가 요청에 대한 결과를 만들어서 응답


**Stateful, Stateless**
* 무상태 프로토콜(Stateless)
  * 서버가 클라이언트의 상태를 보존 X
  * 장점 - 서버 확장성 높음(스케일 아웃)
  * 단점 - 클라이언트가 추가 데이터 전송
* Stateful, Stateless 차이
  * 상태 유지(Stateful) - 항상 같은 서버가 유지되어야한다. 최소한만 사용
  * 무상태(Stateless) - 아무 서버나 호출해도 되어 스케일 아웃(수평 확장)에 유리
  * 실무 한계 - 모든 것을 무상태로 설계할 수 있는 경우도 있고 아닌 경우도 있다.
    * ex) 로그인이 필요없는 단순한 서비스 소개 화면 - 무상태 <br>
    사용자가 로그인한 상태를 (일반적으로 브라우저 쿠키와 서버 세션등을 사용하여) 서버에 유지 - 상태유지

**비연결성(connectionless)**
* HTTP는 기본이 연결을 유지하지 않는 모델
* 일반적으로 초 단위 이하의 빠른 속도로 응답 
* 1시간동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 적음
* 서버 자원을 매우 효율적으로 사용할 수 있음
* 한계와 극복
  * TCP/IP 연결을 새로 맺어야함 - 3 way handshake 시간 추가
  * 웹 브라우저로 사이트를 요청하면 HTML 뿐만 아니라 js, css, 이미지 등 수많은 자원이 함께 다운로드
  * 지금은 HTTP 지속 연결(Persistent Connections)로 문제 해결
  * HTTP/2, HTTP/3에서 더 많은 최적화

**HTTP 메시지**

![Image](https://github.com/user-attachments/assets/5270a607-79a3-4f44-b72e-edf386df2aeb)
* 공식 스펙
```
HTTP-message  = start-line
                *( header-field CRLF )
                CRLF
                [ message-body ]
```

* 시작 라인 (요청 메시지)
  * HTTP 메서드
    * 종류 - GET, POST, PUT, DELETE
    * 서버가 수행해야 할 동작 지정
      * GET - 리소스 조회
      * POST - 요청 내역 처리
  * 요청 대상
    * absolute-path[?query]
    * 절대경로 = `/`로 시작하는 경로
  * HTTP 버전
* 시작 라인 (응답 메시지)
  * HTTP 버전
  * HTTP 상태코드 - 요청 성공, 실패를 나타냄
  * 헤더
    * header-field = field-name ":" OWS field-value OWS (OWS:Optional WhiteSpace)
    * field-name은 대소문자 구분 X
  * 헤더 용도
    * HTTP 전송에 필요한 모든 부가정보 (ex)메시지 바디의 내용, 메시지 바디의 크기, 요청 클라이언트(브라우저)정보 등)
    * 필요시 임의의 헤더 추가 가능
  * 메시지 바디 용도
    * 실제 전송할 데이터
    * HTML 문서, 이미지, JSON 등 byte로 표현할 수 있는 모든 데이터 전송 가능

</details>

---

<details>
  <summary><h3>HTTP 메서드</h3></summary>

**HTTP API**
* API URI 설계에서 가장 중요한 것은 `리소스 식별`
* 리소스 식별, URI 게층 구조 활용
  * ex) /members/{id}
  * URI는 리소스만 식별
    * 리소스(명사)와 리소스를 대상으로 하는 행위(동사)를 분리

**HTTP 메서드 - GET, POST**
* GET
  * 리소스 조회
  * 서버에 전달하고 싶은 데이터는 query를 통해서 전달
  * 메시지 바디를 사용해서 데이터를 전달할 수 있지만 지원하지 않는 곳이 많아서 권장하지 않음
* POST
  * 요청 데이터 처리
  * 메시지 바디를 통해 서버로 요청 데이터 전달
  * 다른 메서드로 처리하기 애매한 경우 사용
  * 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용

**HTTP 메서드 - PUT, PATCH, DELETE**
* PUT
  * 리소스를 대체
    * 리소스가 있으면 대체, 없으면 생성, 쉽게 말해 덮어쓰기
  * *클라이언트가 리소스 식별*
    * 클라이언트가 리소스 위치를 알고 URI 지정
    * POST 와의 차이점
* PATCH
  * 리소스 부분 변경
* DELETE
  * 리소스 제거

**HTTP 기타 메서드 - HEAD, OPTIONS, CONNECT, TRACE**
* HEAD - GET 과 동일하지만 메시지 부분을 제외하고 상태줄과 헤더만 반환
* OPTIONS - 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명(주로 CORS에서 사용)
* CONNECT - 대상 리소스로 식별되는 서버에 대한 터널을 설정
* TRACE - 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행

**HTTP 메서드의 속성**

![Image](https://github.com/user-attachments/assets/f5acfb96-acfb-4cb1-8dd7-20a2d66f618d)

* 안전(Safe Methods)
  * 호출해도 리소스를 변경하지 않는다.
* 멱등(Idempotent Methods)
  * f(f(x)) = f(x)
  * 한번 호출하든 100번 호출하든 결과가 똑같다.
  * 자동 복구 메커니즘
* 캐시가능(Cacheable Methods)
  * GET, HEAD, POST, PATCH 캐시 가능하지만 실제로 GET, HEAD 정도만 캐시로 사용
  * POST, PATCH는 본문 내용까지 캐시 키로 고려해야 하는데, 구현이 쉽지 않음

</details>

---

<details>
  <summary><h3>HTTP 메서드 활용</h3></summary>

**클라이언트에서 서버로 데이터 전송**
* 데이터 전달 방식
  * 쿼리 파라미터를 통한 데이터 전송
    * GET
    * 주로 정렬 필터(검색어)
  * 메시지 바디를 통한 데이터 전송
    * POST, PUT, PATCH
    * 회원 가입, 상품 주문, 리소스 등록, 리소스 변경
* 4가지 상황
  * 정적 데이터 조회
    * 이미지, 정적 텍스트 문서
    * 조회는 GET 사용
    * 정적 데이터는 일반적으로 쿼리 파라미터 없이 리소스 경로로 단순하게 조회 가능
  * 동적 데이터 조회
    * 주로 검색, 게시판 목록에서 정렬 필터(검색어)
    * GET은 쿼리 파라미터 사용해서 데이터 전달
  * HTML FORM을 통한 데이터 전송
    * HTML Form submit 시 POST 전송
      * ex) 회원 가입, 상품 주문, 데이터 변경
    * Content-Type
      * form의 내용을 메시지 바디를 통해서 전송(key=vlaue, 쿼리 파라미터 형식)
      * 전송 데이터를 url encoding 처리
    * HTML Form은 GET, POST만 지원
  * HTTP API를 통한 데이터 전송
    * 회원 가입, 상품 주문, 데이터 변경
    * 서버 to 서버, 앱 클라이언트, 웹 클라이언트(AJAX)
    * POST, PUT, PATCH - 메시지 바디를 통해 데이터 전송
    * GET - 조회, 쿼리 파라미터로 데이터 전달
    * Content-Type: application/json을 주로 사용(사실상 표준)
      * TEXT, XML, JSON 등

**HTTP API 설계 예시**
* HTTP API - 컬렉션(Collection)
  * POST 기반 등록
    * 클라이언트는 등록될 리소스의 URI를 모른다.
    * 서버가 리소스 URI를 생성하고 관리한다.
* HTTP API - 스토어(Store)
  * PUT 기반 등록
    * 클라이언트가 관리하는 리소스 저장소
    * 클라이언트가 리소스 URI를 지정하고 관리한다.
* HTML FORM 사용
  * 웹 페이지 회원 관리
  * GET, POST만 지원
  * 컨트롤 URI
    * 동사로 된 리소스 경로 사용
    * HTTP 메서드로 해결하기 애매한 경우 사용
</details>

---

<details>
  <summary><h3>HTTP 상태코드</h3></summary>

**상태 코드**
* 클라이언트가 보낸 요청의 처리 상태를 응답에서 알려주는 기능
  * 1xx(Informational): 요청이 수신되어 처리중(거의 사용 X)
  <details>
    <summary>2xx(Successful): 요청 정상 처리</summary>
  
    * 200 OK (요청 성공)
    * 201 Created (요청 성공해서 새로운 리소스 생성)
    * 202 Accepted (요청이 접수되었으나 처리가 완료되지 않았음)
      * 배치 처리 같은 곳에서 사용
    * 204 No Content (서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음)
      * ex) 웹 문서 편집기에서 save 버튼의 결과로 아무 내용이 없어도 되고 눌러도 같은 화면을 유지해야한다.
  </details>

  <details>
    <summary>3xx(Redirection): 요청을 완료하려면 유저 에이전트의 추가 행동 필요</summary>
  
    * 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동(리다이렉션)
    * 300 Multiple Choices (사용 X)
    * 301 Moved Permanently (영구 리다이렉션)
      * 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음
    * 302 Found (일시적인 리다이렉션)
      * 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음
    * 303 See Other (일시적인 리다이렉션)
      * 리다이렉트시 요청 메서드가 GET으로 변경
    * 304 Not Modified
      * 캐시를 목적으로 사용
      * 클라이언트에게 리소스가 수정되지 않음을 알려주어 클라이언트는 로컬PC에 저장된 캐시를 재사용(캐시로 리다이렉트)
      * 응답에 메시지 바디를 포함하면 안됨 (로컬 캐시 사용해야하므로)
      * 조건부 GET, HEAD 요청시 사용
    * 307 Temporary Redirect (일시적인 리다이렉션)
      * 리다이렉트시 요청 메서드와 본문 유지(요청 메서드를 변경하면 안된다.)
    * 308 Permanent Redirect (영구 리다이렉션)
      * 리다이렉트시 요청 메서드와 본문 유지(처음 POST를 보내면 리다이렉트도 POST 유지)
    * 일시적인 리다이렉션(302, 303, 307)
      * 처음 302 스펙의 의도는 HTTP 메서드를 유지하는것
      * 웹 브라우저 대부분 GET으로 바꾸어버려 모호한 302 대신 303, 307 등장
      * 303,307 권장하지만 이미 많은 애플리케이션 라이브러리들이 302를 기본값으로 사용하기 때문에 자동 리다이렉션시 GET으로 변해도 되면<br>
      그냥 302를 사용해도 큰 문제 없음
  </details>

  <details>
    <summary>4xx(Client Error): 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음</summary>
  
    * 오류의 원인이 클라이언트에 있음
    * 클라이언트가 이미 잘못된 요청, 데이터를 보내고 있기 때문에 똑같은 재시도가 실패함
    * 400 Bad Request (클라이언트가 잘못된 요청을 해서 서버가 요청을 처리할 수 없음)
      * 요청 구문, 메시지 등등 오류
      * 클라이언트는 요청 내용을 다시 검토하고 보내야함 (ex) 요청 파라미터가 잘못, API 스펙이 맞지 않을때)
    * 401 Unauthorized (클라이언트가 해당 리소스에 대한 인증이 필요함)
      * 인증(Authentication)되지 않음
      * 401 오류 발생 시 응답에 WWW-Authenticate헤더와 함께 인증 방법을 설명
        * 인증(Authentication): 본인이 누구인지 확인(로그인)
        * 인가(Authorization): 권한부여(ADMIN처럼 특정 리소스에 접근할 수 있는 권한, 인증이 있어야 인가가 있음)
    * 403 Forbidden (서버가 요청을 이해했지만 승인을 거부함)
      * 주로 인증 자격 증명은 있지만 접근 권한이 불충분한 경우 (ex) 어드민 등급이 아닌 사용자가 로그인은 했지만 어드민 등급의 리소스에 접근하는 경우)
    * 404 Not Found (요청 리소스를 찾을 수 없음)
      * 요청 리소스가 서버에 없음
      * 또는 클라이언트가 권한이 부족한 리소스에 접근할 때 해당 리소스를 숨기고 싶을때
  </details>

  <details>
    <summary>5xx(Server Error): 서버 오류, 서버가 정상 요청을 처리하지 못함</summary>

    * 서버에 문제가 있기 때문에 재시도 하면 성공할 수도 있음
    * 500 Internal Server Error (서버 문제로 오류 발생, 애매하면 500 오류)
    * 503 Service Unavailable (서비스 이용 불가)
      * 서버가 일시적인 과부하 또는 예정된 작업으로 잠시 요청을 처리할 수 없음
      * Retry-After 헤더 필드로 얼마뒤에 복구되는지 보낼 수 있음
  </details>
  
* 만약 모르는 상태코드가 나타나면?
  * 클라이언트는 상위 상태코드로 해석해서 처리
    * ex) 299 -> 2xx(Successful), 451 -> 4xx(Client Error)
</details>

---

<details>
  <summary><h3>HTTP 헤더 : 일반 헤더</h3></summary>

**HTTP BODY**
* message body - RFC7230
  * 메시지 본문(message body)을 통해 표현 데이터 전달
  * 메시지 본문 = 페이로드(payload)
  * 표현은 요청이나 응답에서 전달할 실제 데이터
  * 표현 헤더는 표현 데이터를 해석할 수 있는 정보 제공
    * 데이터 유형(html, json), 데이터 길이, 압축 정보 등

**표현**
* Content-Type - 표현 데이터의 형식 설명
  * 미디어 타입, 문자 인코딩  
  ex) text/html; charset=utf-8, applicatoin/json, image/png
* Content-Encoding - 표현 데이터 인코딩
  * 표현 데이터를 압축하기 위해 사용
  * 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가
  * 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제  
  ex) gzip, defalte, identity
* Content-Language - 표현 데이터의 자연 언어
  * 표현 데이터의 자연 언어를 표현  
  ex) ko, en, en-US
* Content-Length - 표현 데이터의 길이
  * 바이트 단위
  * Transfer-Encoding(전송 코딩)을 사용하면 Content-Length를 사용하면 안됨
* 표현 헤더는 전송, 응답 둘다 사용

**협상(컨텐츠 네고시에이션)**
* Accept: 클라이언트가 선호하는 미디어 타입 전달
  * 구체적인것이 우선순위
* Accept-Charset: 클라이언트가 선호하는 문자 인코딩
* Accept-Encoding: 클라이언트가 선호하는 압축 인코딩 (압축전송)
* Accpet-Language: 클라이언트가 선호하는 자연 언어 (단순전송)
  * Quality Values(q) 값 사용하여 0~1 클수록 높은 우선순위
* 협상 헤더는 요청시에만 사용

**일반 정보**
* From: 유저 에이전트의 이메일 정보
  * 일반적으로 잘 사용되지 않음
  * 검색 엔진 같은곳에서 주로 사용
* Referer: 이전 웹 페이지 주소
  * A -> B로 이동하는 경우 B를 요청할때 Referer: A를 포함해서 요청
  * referrer의 오타이지만 이미 너무 많이 쓰고 있어서 오타 그대로 사용하기로함
* User-Agent: 유저 에이전트 애플리케이션 정보
  * 클라이언트의 애플리케이션 정보
  * 통계 정보
  * 어떤 브라우저에서 장애가 발생하는지 파악 가능
* Server: 요청을 처리하는 오리진 서버의 소프트웨어 정보
* Date: 메시지가 생성된 날짜

**특별한 정보**
* Host: 요청한 호스트 정보(도메인)
  * 하나의 서버가 여러 도메인을 처리해야할때
  * 하나의 IP 주소에 여러 도메인이 적용되어 있을때
* Location: 페이지 리다이렉션
* Allow: 허용 가능한 HTTP 메서드
  * 405(Method Not Allowed)에서 응답에 포함해야함
  * Allow: GET, HEAD, PUT
* Retry-After: 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간

**인증**
* Authorization: 클라이언트 인증 정보를 서버에 전달
* WWW-Authenticate: 리소스 접근시 필요한 인증 방법 정의

**쿠키**
* Set-Cookie: 서버에서 클라이언트로 쿠키 전달(응답)
* Cookie: 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달
  * 사용처
    * 사용자 로그인 세션 관리
    * 광고 정보 트래킹
  * 쿠키 정보는 항상 서버에 전송됨
    * 네트워크 트래픽 추가 유발
    * 최소한의 정보만 사용(세션 id, 인증 토큰)
    * 서버에 전송하지 않고, 웹 브라우저 내부에 데이터를 저장하고 싶으면 웹 스토리지(localStorage, sessionStorage)참고
  * 주의
    * 보안에 민감한 데이터는 저장하면 안됨(주민번호, 신용카드 번호 등)
* 생명주기
  * expires: 만료일이 되면 쿠키 삭제
  * max-age: 0이나 음수를 지정하면 쿠키 삭제
  * 세션 쿠키: 만료 날짜를 생략하면 브라우저 종료시까지만 유지
  * 영속 쿠키: 만료 날짜를 입력하면 해당 날짜까지 유지
* 도메인(Domain)
  * 명시: 명시한 문서 기준 도메인 + 서브 도메인 포함
  * 생략: 현재 문서 기준 도메인만 적용
* 경로(Path)
  * 일반적으로 path=/ 루트로 지정
  * 이 경로를 포함한 하위 경로 페이지만 쿠키 접근
* 보안
  * Secure
    * 쿠키는 http, https를 구분하지 않고 전송
    * Secure를 적용하면 https인 경우에만 전송
  * HttpOnly
    * XSS공격 방지
    * 자바스크립트에서 접근 불가(document.cookie)
    * HTTP 전송에만 사용
  * SameSite
    * XSRF 공격 방지
    * 요청 도메인과 쿠기에 설정된 도메인이 같은 경우만 쿠키 전송
</details>

---

<details>
  <summary><h3>HTTP 헤더 : 캐시와 조건부 요청</h3></summary>

**
</details>