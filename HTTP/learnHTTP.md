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

<img src="![Image](https://github.com/user-attachments/assets/be1e6e47-17f5-4b6f-a134-c2f70c14331f)">


**웹 브라우저 요청 흐름**
</details>