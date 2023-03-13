# Web의 동작 원리 - 클라이언트와 서버의 만남

## 목차

- Web의 등장
- 클라이언트와 서버
- HTTP와 URL
- 쿠키와 세션
- IP, Port 그리고 DNS

<hr/>

# Web의 등장

옛날에는 전화선을 이용하는 PC통신을 했지만, 영국의 컴퓨터 과학자 팀 버너스 리(Sir Tim Berners-Lee)가 1989년 World Wide Web을 고안하게 됨.
<br/><br/>

PC 통신과 Web의 차이점

| PC 통신     | Web        |
| ----------- | ---------- |
| 폐쇄        | 개방       |
| 저속        | 고속       |
| 전화선/모뎀 | 광랜(FTTH) |

<br/>

### Web 1.0

- 1990년대 후반 ~ 2000년대<br/>
  => 어느 누구나 프로그램을 대중에게 공개할 수 있는 세상이 도래.<br/>
  수많은 서비스가 탄생한만큼 도태되고 사라지는 서비스도 많았다.

### Web 2.0

2010년대 ~ 현재<br/>

- 일방향적으로 정보를 제공받넌 사용자 => 직접 정보를 생산하고 공유하게 됨.

- 스마트폰의 등장으로 대부분의 서비스가 스마트폰에 최적화되어서 나오고 SNS도 등장을 하게 됨.

### Web 3.0

현재 ~ <br/>

- 데이터의 투명한 공개. <br/>
  ex) 블록 체인(분산 컴퓨팅 기술 기반의 데이터 위변조 방지 기술)<br/>
- 느린 네트워크 처리 속도
- 오픈소스 형태이기 때문에 책임자 불분명함.

<hr/>
<br/>

# 클라이언트와 서버

<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/client.png?raw=true">
클라이언트(client): 요청을 보내는 주체

<hr/>
<br/>

# HTTP 통신과 URL

HTTP(Hyper Text Transfer Protocol): 인터넷에서, 웹 서버와 사용자의 인터넷 브라우저 사이에 문서를 전송(Transfer)하기 위해 사용되는 통신 규약(Protocol)<br/><br/>
<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/http.png?raw=true">
=> 웹은 html 언어로 되어있고 응답받는 요소중 하나이다.
<br/>
<br/>
<br/>
URL(Uniform Resource Locator): 한 인터넷 서버(즉 웹 페이지)에서 주관하는 자원에 접근할 수 있는 모든 데이터.
<br/>
<br/>

<span style="background-color:#fff5b1">https://</span>www.google.com/search?q=techit

### 프로토콜(Protocol)

- 통신 규칙
- HTTP(HTTPS), FTP 등
  <br/>
  <br/>

https://<span style="background-color:#DCFFE4">www.google.com</span>/search?q=techit

### 호스트(Host)

- 서버의 주소
- google.com을 호스트 네임이라고 지칭
  <br/>
  <br/>

https://www.google.com<span style="background-color:#E6E6FA">/search</span>?q=techit

### 경로(Path)

- 호스트 내 서비스의 위치
- 서비스 별로 분할 ex) 검색, 회원 등
  <br/>
  <br/>

https://www.google.com/search<span style="background-color:#F5F5F5">?q=techit</span>

### 쿼리 문자열(Query String)

- ? 기호로 시작. &로 연결
- 키/값 쌍으로 구성
<br/>
<br/>
<hr/>
<br/>

# 쿠키와 세션

<br/>

### 쿠키

- 쿠키는 클라이언트(브라우저) 로컬에 저장되는 키와 값이 들어있는 작은 데이터 파일입니다.

- 사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지된다는 특징이 있습니다.
- 쿠키는 클라이언트의 상태 정보를 로컬에 저장했다가 참조합니다.
- 클라이언트에 300개까지 쿠키저장 가능, 하나의 도메인당 20개의 값만 가질 수 있음, 하나의 쿠키값은 4KB까지 저장합니다.
- Response Header에 Set-Cookie 속성을 사용하면 클라이언트에 쿠키를 만들 수 있습니다.
- 쿠키는 사용자가 따로 요청하지 않아도 브라우저가 Request시에 Request Header를 넣어서 자동으로 서버에 전송합니다.

<br/>

### 쿠키의 구성 요소

- 이름 : 각각의 쿠키를 구별하는 데 사용되는 이름

- 값 : 쿠키의 이름과 관련된 값
- 유효시간 : 쿠키의 유지시간
- 도메인 : 쿠키를 전송할 도메인
- 경로 : 쿠키를 전송할 요청 경로

<br/>
<br/>

### 세션

<br/>

- 세션은 쿠키를 기반하고 있지만, 사용자 정보 파일을 브라우저에 저장하는 쿠키와 달리 세션은 서버 측에서 관리합니다.
- 서버에서는 클라이언트를 구분하기 위해 세션 ID를 부여하며 웹 브라우저가 서버에 접속해서 브라우저를 종료할 때까지 인증상태를 유지합니다.
- 물론 접속 시간에 제한을 두어 일정 시간 응답이 없다면 정보가 유지되지 않게 설정이 가능 합니다.
- 사용자에 대한 정보를 서버에 두기 때문에 쿠키보다 보안에 좋지만, 사용자가 많아질수록 서버 메모리를 많이 차지하게 됩니다.
- 즉 동접자 수가 많은 웹 사이트인 경우 서버에 과부하를 주게 되므로 성능 저하의 요인이 됩니다.
- 클라이언트가 Request를 보내면, 해당 서버의 엔진이 클라이언트에게 유일한 ID를 부여하는 데 이것이 세션 ID입니다.
  <br/>

  <img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/cookie.png?raw=true">
  <br/>

### 세션의 동작 방식

- 클라이언트가 서버에 접속 시 세션 ID를 발급 받음

- 클라이언트는 세션 ID에 대해 쿠키를 사용해서 저장하고 가지고 있음
- 클라리언트는 서버에 요청할 때, 이 쿠키의 세션 ID를 같이 서버에 전달해서 요청
- 서버는 세션 ID를 전달 받아서 별다른 작업없이 세션 ID로 세션에 있는 클라언트 정보를 가져와서 사용
- 클라이언트 정보를 가지고 서버 요청을 처리하여 클라이언트에게 응답
  <br/>

<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/session.png?raw=true">
<br/>

<br/>
<hr/>
<br/><br/>

# IP, Port 그리고 DNS

### 네트워크

- 두대 이상의 컴퓨터가 연결된 통신망

### 네트워크의 구성요소

- 호스트(Host): 구성된 네트워크에서 연결된 개별 컴퓨터

- 스위치(switch): 많은 컴퓨터를 연결하기 위한 매개체
- 라우터(router): 서로 다른 네트워크 간의 통신을 위한 장비

<br/>
<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/internet.png?raw=true">
=> 이렇게 거대하게 연결된 네트워크를 인터넷이라 한다.

<br/>

## IP (Internet Protocol)

- 컴퓨터 간 데이터를 주고받는 네트워크 계층의 규약

- 데이터 전달에 필요한 <span style="color:yellow">목적지 컴퓨터 정보</span>가 필요하다.

## IP 주소

- 네트워크에서 컴퓨터가 부여받는 고유한 주소

## IPv4 vs IPv6

<br/>

| 구분        | IPv6                                    | IPv4                   |
| ----------- | --------------------------------------- | ---------------------- |
| 주소길이    | 128 비트                                | 32비트                 |
| 주소 형태   | 2001:0db8:85a3:08d3:1319:8a2e:0370:7334 | 221.23.222.222         |
| 주소 개수   | 2의 128승개 (43억 x 43억 x 43억 x 43억) | 2의 32승개 (약 43억개) |
| 패킷 헤더   | 고정 사이즈                             | 변동 사이즈            |
| 헤더 필드수 | 12                                      | 8                      |
| P&P 기능    | 자동 구성으로 지원                      | 없음                   |
| 이동성      | 가능                                    | 상당히 곤란            |

<br/>

11000000101010000000000000000011
<br/>
=> 32비트 주소를 8비트씩 분할
<br/>
11000000 | 10101000 | 00000000 |00000011
<br/>
=> 2진수를 10진수로 변환
<br/>
192.168.0.3

<br/>

각 마디의 숫자는 0부터 255로 구성되어 있다.

- 0.0.0.0 ~ 255.255.255.255

<br/>

## 공인 IP vs 사설 IP

<br/>

### 공인 IP (Public IP)

- 전체 인터넷 망에서 고유하게 식별 가능한 주소

- IPv4 체계에서 자원 부족
- 하나의 공인 IP에서 수많은 사설 IP 할당이 가능

<br/>

### 사설 IP (Private IP)

- 가정의 LAN과 같은 네트워크에서 할당되는 주소

- 컴퓨터에서 조회되는 IP

<br/>

<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/isp.png?raw=true">

<br/>

### 127.0.0.1

- localhost: 컴퓨터의 관점에서 자기 자신을 가리키기 위해 약속된 주소 <br/>
  => 자신의 컴퓨터에서만 유효함.

<br/>

<img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/ip.png?raw=true">
<br/>
<br/>

## Port

- 컴퓨터가 각종 신호, 정보 등을 주고 받을 수 있도록 해주는 통신 통로 (=컴퓨터의 도로)

- 여러 네트워크 활동 (ex. 업로드, 다운로드 등)을 할 때 사용하는 관문 같은 역할

- 컴퓨터 안에서 프로그램을 찾기 위한 수단, 즉 각 프로세스가 위치한 방 번호라고 생각하면 됨

- 즉, 다양한 서비스를 구분하는 역할!

<br/>

| Protocol | 포트 번호 |
| -------- | --------- |
| HTTP     | 80        |
| HTTPS    | 443       |
| SMTP     | 25        |
| FTP      | 21        |

=> Protocol과 포트번호

<br/>
<br/>

## DNS (Domain Name Server)

- URl을 해석하여 IP 주소로 변환하는 서버

- 도메인은 IP 주소를 대신하여 사용하는 주소이다.
- DNS라는 시스템을 이용해서 IP와 도메인을 매칭한다.
- DNS란 웹사이트의 IP 주소와 도메인 주소를 이어주는 환경/시스템이다.
- DNS 시스템 안에서 IP와 도메인 매칭을 하는 역할을 하는 것이 DNS 서버이다.
- DNS 서버와 네임서버는 같은 의미이다.
- 국가, 기업등이 운영을 하고 전세계 DNS는 연결되어 있다. 따라서, 장애 발생 시 막대한 피해로 이어진다.

<br/>

  <img src="https://github.com/WestSilver99/Daily_Study/blob/main/Web/img/dns.png?raw=true">
