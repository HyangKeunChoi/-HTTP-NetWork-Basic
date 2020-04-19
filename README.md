# 그림으로 배우는 HTTP&NetWork

## 제 1장 웹과 네트워크의 기본에 대해 알아보자

### 1.1 웹은 HTTP로 나타낸다

+ 웹 브라우저는 웹브라우저 주소 입력란에 지정된 URL에 의지해서 웹 서버로부터 리소스라고 불리는 파일 등의 정보를 얻는다.
+ 클라이언트에서 서버까지 일련의 흐름을 결정하고 있는 것은 웹에서 HTTP(HyperText Transfer Protocol)이라 불리는 프로토콜이다.
+ 프로토콜이라는 의미는 "약속"이다.
+ HTTP/1.1 : 현재 가장 많이 사용되는 버전

### 1.3.2 계층으로 관리하는TCP/IP
+ TCP/IP : 인터넷과 관련된 프로토콜들을 모은 것
  - TCP/IP는 애플리케이션 계층, 트랜스포트 계층, 네트워크 계층, 링크 계층 이렇게 4계층으로 나뉘어있다.
  - 계층화 이유 : 1. 사양이 변경된 계층만 바꿀 수 있다
                  2. 각 계층은 계층이 연결되어 있는 부분만 결정되어 있어, 각 계층의 내부는 자유롭게 설계할 수 있다.
                  3. 계층화하면 설계를 편하게 할 수 있다.
+ 애플리케이션 계층
  - 유저에게 제공되는 애플리케이션에서 사용하는 통신의 움직임을 결정
  - FTP랑 DNS, HTTP 도 애플리케이션 계층에 포함
+ 트랜스포트 계층
  - 트랜스포트 계층은 애플리케이션 계층에 네트워크로 접속되어 있는 2대의 컴퓨터 사이의 데이터 흐름을 제공
  - TCP / UDP 두가지 프로토콜 존재
+ 네트워크 계층(인터넷 계층)
  - 네트워크 상에서 패킷의 이동을 다룹니다.
  - 패킷이란 전송하는 데이터의 최소단위
  - 어떤 경로를 거쳐 상대방의 컴퓨터까지 패킷을 보낼지를 결정
+ 링크 계층(데이터 링크 계층, 네트워크 인터페이스 계층)
  - 네트워크에 접속하는 하드웨어적인 면을 다룹니다.
  - 운영체제가 하드웨어를 제어하기 때문에 디바이스 드라이버랑 네트워크 인터페이스 카드를 포함
  - 케이블과 같이 물리적으로 보이는 부분도 포함

### 1.3.3 TCP/IP 통신의 흐름
+ 송신하는 측은 애플리케이션 계층에서부터 내려가고, 수신하는 측은 애플리케이션 계층으로 올라갑니다.
+ 순서(송신) : 송신측 클라이언트의 애플리케이션 계층(HTTP)에서 어느 웹 페이지를 보고 싶다라는 HTTP 리퀘스트를 지시, 
그 다음에 있는 트랜스포트계층(TCP)에서 애플리케이션계층에서 받은 데이터를 통신하기 위해 조각내어 안내번호와 포트를 붙여
네트워크계층에 전달, 네트워크 계층(IP)에서는 수신지 MAC주소를 추가해서 링크 계층으로 전달
+ 순서(수신) : 수신 측 서버는 링크 계층에서 데이터를 받아들여 순서대로 위의 계층에 전달하여 애플리케이션 계층까지 도달

+ 송신할떄 각 계층을 거칠때 , 해당 계층마다 필요한 정보를 추가 반대로 수신측에서 각 계층을 거칠 떄마다 사용한 헤더를 삭제 이를 **캡슐화 라고함**

### 1.4.1 배송을 담당하는 IP
+ IP : 인터넷 프로토콜 /  IP주소(IP Address) : 각 노드에 부여된 주소
+ IP의 역할은 개개의 패킷을 상대방에게 전달하는 것
+ 상대방에게 전달하기까지 IP주소와 MAC주소라는 요소가 중요
+ ARP(Address Resolution Protocol)이라는 프로토콜을 이용하여 다음 중계할 곳의 MAC주소를 사용하여 목적지를 찾아간다. 

### 1.4.2 신뢰성 있는 TCP
+ 바이트 스트림 서비스 : 용량이 큰 데이터를 보내기 쉽게 TCP 세그먼트라고 불리는 단위 패킷으로 작게 분해하여 관리하는 것

#### Three way handshaking
+ SYN 플래그 : 송신측에서 접속함과 동시에 패킷을 보냄
+ SYN/ACK 플래그 : 수신측에서 SYN/ACK 플래그로 송신측에 접속함과 동시에 패킷을 수신한 사시을 전한다.
+ 마지막으로 송신측이 'ACK'플래그를 보내 패킷 교환이 완료되었음을 전한다.

### 1.5 이름 해결을 담당하는 DNS


### 1.7 URI와 URL
+ URL(Uniform Resource Locator)
+ URI(Uniform Resource Identifiers) 

##### Uniform
통일(Uniformity)된 서식을 결정하는 것으로, 여러 가지 종류의 리소스 지정 방법을 같은 맥락에서 구별없이 취급

또한, 새로운스키마 http와 ftp 등 도입을 용이하게 한다.

##### Resource

리소스는 '식별 가능한 모든 것'이라고 정의 되어 있습니다. 도큐먼트 파일뿐만 아니라 이미지와 서비스 등 다른 것과 구별할 수 있는
것은 모두 리소스 입니다. 또한 리소스는 단일한 부분만 아니라 복수의 집합도 리소스로 파악할 수 있습니다.

##### Identifier
식별 가능한 것을 참조하는 오브젝트이며 식별자로 불립니다. 결국 URI는 스키마를 나타내는 리소스를 식별하기 위한 식별자 입니다.

URI는 리소스를 식별하기 위해 문자열 전반을 나타내는데 비해 URL은 리소스의 장소(네트워크 상의 위치)를 나타냅니다.
URL은 URI의 서브셋입니다.

## 제2장 간단한 프로토콜 HTTP

### 2.3 HTTP는 상태를 유지하지 않는 프로토콜

+ HTTP는 상태를 계속 유지하지 않는 스테이트리스(stateless) 프로토콜 입니다.
+ 리퀘스트와 리스폰스를 교환하는 동안에 상태를 관리하지 않습니다. 즉, HTTP프로토콜 레벨에서는 이전에 보냈던 리퀘스트나
이미 되돌려준 리스폰스에 대해서는 전혀 기억하지 않습니다.
+ 상태를 계속 유지하고 싶은 요구에 부응하기 위해서 쿠키(Cookie)라는 기술이 도입되었습니다.

### 2.4 리퀘스트 URI로 리소스를 식별
+ HTTP는 URI(Uniform Resource Identifiers)를 사용하여 인터넷 상의 리소스를 지정합니다.

### 2.5 서버에 임무를 부여하는 HTTP 메소드

#### GET
+ get 메소드는 리퀘스트 URI로 식별된 리소스를 가져 올 수 있도록 요구합니다.

#### Post
+ Post메소드는 엔티티를 전송하기 위해서 사용됩니다.
+ Post는 Get과 비슷하지만 리스폰스에 의한 엔티티를 획득하는 것만이 목적은 아닙니다.

#### Put
+ Put 메소드는 파일을 전송하기 위해서 사용됩니다.
+ FTP에 의한 파일 업로드와 같이, 리퀘스트 중에 포함된 엔티티를 리퀘스트 URI로 지정한 곳에 보존하도록 요구합니다.

#### Head
+ Head메소드는 Get과 같은 기능이지만 메시지 바디를 돌려주지 않습니다.
+ URI 유효성과 리소스 갱신 시간을 확인하는 목적 등으로 사용됩니다.

#### DELETE 
+ DELETE메소드는 파일을 삭제하기 위해 사용됩니다.
+ Put메소드와 반대로 동작합니다.

#### OPTIONS
+ OPTIONS메소드는 리퀘스트 URI로 지정한 리소스가 제공하고 있는 메소드를 조사하기 위해 사용

#### TRACE
+ TRACE메소드는 Web서버에 접속해서 자신에게 통신을 되돌려 받는 루프백을 발생시킵니다.
+ 클라이언트는 TRACE메소드를 사용함으로써, 리퀘스트를 보낸 곳에 어떤 리퀘스트가 가공되어 있는지 등을 조사할 수 있습니다.

#### Connect
+ Connect 메소드는 프록시에 터널 접속 확립을 요함으로써, TCP 통신을 터널링 시키기 위해서 사용합니다.

### 2.8 쿠키를 사용한 상태 관리
+ 무상태 프로토콜(Stateless)를 보안하기 위해 탄생

## 제3장 HTTP정보는 HTTP 메시지에 있다.

+ HTTP 메시지는 메시지 헤더와 메시지 바디로 구성되어있다.
+ 리퀘스트 메시지 헤더 : 리퀘스트 라인, 리퀘스트 헤더 필드, 일반 헤더 필드. 엔티티 헤더 필드
+ 리스폰스 메시지 헤더 : 상태 라인, 리스폰스 헤더 필드, 일반 헤더 필드, 엔티티 헤더 필ㄷ르

+ 리퀘스트 라인 : 리퀘스트에 사용하는 메소드와 리퀘스트 URI와 사용하는 HTTP 버전이 포함
+ 상태 라인 : 리스폰스 결과를 나타내는 상태 코드와 설명, 사용하는 HTTP 버전이 포함
+ 헤더 필드 : 리퀘스트와 리스폰스의 여러 조건과 속성등을 나타내는 각조 헤더 필드가 포함

#### 3.3.1 메시지 바디와 엔티티 바디의 차이

+ 메시지 : HTTP 통신의 기본 단위로 옥텟 시퀀스로 구성되고 통신을 통해서 전송됩니다.
+ 엔티티 : 리퀘스트랑 리스폰스의 페이로드(부가물)로 전송되는 정보로 엔티티 헤더 필드와 엔티티 바디로 구성됩니다.

+ 멀티파트 : 여러 다른 종류의 데이터를 수용
+ 리줌(resume) : 다운로드하다가 끈기면 끈긴 지점부터 다운로드 재개할 수 있다.
+ 레인지 리퀘스트 : 위 기능을 실현하기위해 범위를 지정하여 리퀘스트 하는 것

### 3.6 최적의 콘텐츠를 돌려주는 콘텐츠 네고시에이션
+ 구글 웹 페이지에서는 영어와 한국어와 같이 서로 다른언어를 주로 사용하는 브라우저가 같은 URI에 액세스할 때에
각각 영어판 웹 페이지와 한국어판 웹 페이지를 표시합니다. 이와 같은 구조를 콘텐츠 네고시에이션이라고 부릅니다.
+ 콘텐츠 네고시에이션은 제공하는 리소스를 언어와 문사 세트, 인코딩 방식 등을 기준으로 판단

##### 콘텐츠 네고시에이션에는 다음과 같은 종류들이 있다.
+ 서버 구동형 네고시에이션(Server-driven Negotiation) : 서버 측에서 콘텐츠 네고시에이션 하는 방식
+ 에이전트 구동형 네고시에이션(Agent-driven Negotiation) : 클라이언트 측에서 콘텐츠 네고시에이션 하는 방식
+ 트랜스페어런트 네고시에이션(Transparent Negotitation) : 서버 구동형과 에이전트 구동형을 혼합한 방식

## 제 4장 결과를 전달하는 상태 코드

> 리스폰스의 클래스는 다음과 같이 5개가 정의
+ 1xx : informational 클래스, 리퀘스트를 받아들여 처리중
+ 2xx : Success 클래스, 리퀘스트를 정상적으로 처리 했음
+ 3xx : Redirection 클래스, 리퀘스트를 완료하기 위해서 추가 동작이 필요
+ 4xx : Client Error클래스, 서버는 리퀘스트 이해 불가능
+ 5xx : Server Error클래스, 서버는 리퀘스트 처리 실패

#### 4.2 2xx 성공
+ 200 : 성공
+ 204 : 리퀘스트 성공, 하지만 돌려줄 리소스가 없다.
+ 206 : 부분 지정된 범위의 엔티티가 포함

#### 4.3 3xx 리다이렉트
+ 301 : 새로운 URI가 부여되어 있다.
+ 302 : 301과 달리 일시적
+ 303 : 302과 같은 기능이지만 Get메소드로 얻어야 한다.
+ 304 : 리소스는 있지만 조건이 맞지않는 경우

#### 4.4 4xx 클라이언트 에러
+ 400 : 잘못된 리퀘스트
+ 401 : 인증이 필요
+ 403 : 엑세스 거부 (권한)
+ 404 : 서버상에 없다.

#### 4.5 5xx 서버 에러
+ 500 : 리퀘스트를 처리하는 도중 에러가 발생
+ 503 : 서버 과부하

## 제5장 HTTP와 연계하는 웹 서버

+ 가상 호스트라는 기능을 통해 1대의 서버에서 여러 도매인을 가질 수 있다.

### 5.2 통신을 중계하는 프로그램

+ 프록시 : 서버와 클라이어트의 양쪽 역할을 하는 중계 프로그램으로, 클라이언트로부터의 리퀘스트를 서버에 전송하고, 서버로부터의 리스폰스를
클라이언트에 전송합니다.

+ 게이트웨이 : 다른 서버를 중계하는 서버로, 클라이언트로부터 수신한 리퀘스트를 리소스를 보유한 서버인 것처럼 수신합니다. 경우에 따라서
클라이언트는 상대가 게이트웨이라는 것을 알지 못하는 경우도 있습니다.

+ 터널 : 서로 떨어진 두 대의 클라이언트와 서버 사이를 중계하며 접속을 주선하는 중계 프로그램입니다.

### 5.2.1 프록시
+ 프록시 서버를 사용하는 이유는 나중에 설명할 캐시를 사용해서 네트워크 대역등을 표율적으로 사용하는 것과 조직 내에 특정 웹사이트에 대한
액세스 제한, 액세스 로그를 획득하는 정책을 지키려는 목적

##### 프록시의 사용 방법 2가지
+ 캐시하는지 안하는지 여부
+ 메시지를 변경하는지 안하는지 여부

+ 캐싱 프록시 : 프록시 서버상에 리소스 캐시를 보존해 두는 타입의 프록시
  - 프록시에 같은 리소스에 대한 리퀘스트가 온 경우, 오리진 서버로부터 리소스를 획득하는 것이 아닌 캐시를 리스폰스로 돌려주는 것
+ 투명 프록시 : 중계할 때 메시지를 변경하지 않는 타입의 프록시

### 5.2.2 게이트웨이
+ HTTP 서버 이외의 서비스를 제공하는 서버
+ 클라이언트와 게이트웨이 사이를 암호화하는 등으로 앉ㄴ하게 접속함으로써 통신의 안전성을 높이는 역할

### 5.2.3 터널
+ 터널은 요구에 따라 다른 서버와의 통신 경로를 확립
+ 클라이언트는 SSL과 같은 암호화 통신을 통해 서버와 안전하게 통신을 하기 위해 사용
+ 터널자체는 HTTP 리퀘스트를 해석 X

### 5.3 리소스를 보관하는 캐시
+ 캐시는 프록시 서버와 클라이언트의 로컬 디스크에 보관된 리소스의 사본을 가르킨다.
+ 캐시를 사용하면 리소스를 가진 서버에의 액세스를 줄일 수 있다.
+ 캐시서버는 프록시 서버의 하나로 캐싱 

### 5.3.2 클라이언트 측에도 캐시가 있다.
+ 인터넷 익스플로러에서 클라이언트가 보존하는 캐시를 인터넷 임시 파일이라고 부릅니다.
