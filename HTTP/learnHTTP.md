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