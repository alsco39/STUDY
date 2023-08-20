# HTTP

![images_sujeong_post_855e158c-3d42-4c4f-99b2-7819a6c77d14_image](https://user-images.githubusercontent.com/103401813/168468110-64bac3a9-2148-4d3f-a412-212fd91adaa0.png)

서버와 클라이언트가 텍스트 기반의 통신 규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜

- 규약이 정해져 있어 프로그램이 규약에 맞춰 서로 정보 교환 가능
- HTTP는 어떤 종류의 데이터도 전송 가능
- 클라이언트가 요청(request)하면 서버가 요청 처리 후 응답(response) 하는 방식으로 동작
  - 응답 후 클라이언트와 연결을 끊어 서버는 클라이언트 이전상황을 알 수 없다

**프로토콜(Protocol)**

**표준화된 절차**를 서술한 규칙의 체계

- 일반적으로 통신 프로토콜을 의미
  - 통신 프로토콜 : 컴퓨터나 원거리 통신 장비에서 메시지를 주고 받는 양식과 규칙의 체계

**서버(Server)**

어떠한 자료에 대한 접근을 관리하는 네트워크 상의 시스템(요청에 대한 응답을 보내준다)

= 클라이언트에게 여러 가지 서비스를 제공

**클라이언트(Client)**

네트워크가 연결되어 있는 서버로부터 정보를 제공받는 컴퓨터

- 포괄적으로 컴퓨터 사용자 또한 클라이언트라고 보기도 한다.

URL(Uniform Resource Locator) : 인터넷에서 웹 페이지, 이미지, 비디오 등 리소스의 위치를 가리키는 문자열

- HTTP 맥락에서 웹 주소 또는 링크라고 불린다

DNS(Domain Name System) : 웹사이트의 IP 주소와 도메인 주소를 이어주는 환경, 시스템

- 이 안에서 부분적으로 자기의 역할을 하는 서버를 DNS 서버라고 한다
- 네임서버라고도 한다
- 도메인 : 웹 브라우저를 통해 특정 사이트 진입 시,  IP 주소를 대신해 사용하는 주소
- DNS 서버 : IP 주소와 도메인 주소를 연결해주는 역할

## HTTP 메소드

메소드는 클라이언트가 서버에 데이터를 용철할 때 사용

**[ 주요 메소드 ]**

- GET : 데이터를 읽거나 검색할 때 사용
- POST : 주로 새로운 리소스를 생성할 때 사용
- PUT : 리소스의 모든 것을 업데이트한다.
  - 요청이 오지 않은 것은 null 값으로 변한다
- PATCH : 리소스의 일부를 업데이트한다.
- DELETE : 리소스 삭제

## HTTP 상태코드 (Status Code)

클라이언트가 보낸 HTTP요청에 대한 서버의 응답 코드

1. **1XX(조건부응답)**

서버가 요청을 받았으며 클라이언트는 작업을 계속 진행 하라는 의미

- 100(Continue) : 진행 중, 클라이언트의 작업이 완료되었다면 무시 가능

1. **2XX(성공)**

요청을 성공적으로 받았으며 인식했고 수용함을 의미

- 200 OK (Success) : 성공적으로 처리된 경우
- 201 Created : 요청이 정상적을 수행되었고, 리소스가 새로 생성되었다는 것을 의미
- 204 NO Content : 요청이 정상적으로 수행되었고, 요청과 관련된 컨텐츠 또한 존재하지 않음을 의미

1. **3XX(Redirection 리다이렉션 완료)**

리다이렉션(다시 지시하는 것)과 관련된 상태들 의미

[ 클라이언트가 요청한 리소스에 접근이 불가능하여 다른 URL을 통해 리소스에 접근가능 한 경우 사용 ]

- 301 Moved Permanetly : = 301 Redirect 라고도 불린다. 가장 많이 사용된다.
- 304 Noot Modified : 클라이언트가 요청한 리소스가 이전 요청때와 전혀 달라진 점이 없다는 것을 의미

1. **4XX(Client error 클라이언트 에러)**

클라이언트가 서버에게 보낸 요청이 잘못된 경우를 의미

- 400 Bad Request : 클라이언트가 요청을 잘못 보냄을 의미
- 401 Unauthorized : 인증되지 않은 사용자가 인증이 필요한 리소스를 요청한 경우 인증이 필요하다고 알려주는 상태 코드
- 403 Poebidden : 클라이언트가 접근이 금지된 리소스를 요청했음을 의미

1. 5XX(Server Error 서버 오류)

올바른 요청에 대해 서버가 응답할 수 없다 = 서버에 문제가 생겼다

- 500 Internal Server Error : 백엔드 어플리케이션 내에서 알 수 없는 에러가 발생
- 502 Bad Gateway : 백엔드 어플리케이션이 문제가 생긴 상황
- 503 Service Unavailable : 서버가 요청을 처리한 준비가 되지 않았다

## HTTP 보안

HTTP는 통신 상대를 확인하지 않아 누구든 요청이 가능하고 요청 대상이 접근 권한 처리를 안 한 경우 응답을  반환한다.

- 통신 상대를 확인하지 않기 때문에 <u>디도스 공격</u>에 취약하다.
- DDoS(Distributed Denial of Service sttack) 는 특정 서버(컴퓨터)나 네트워크 장비를 대상으로 많은 데이터를 발생시켜 장애를 일으키는 대표적인 서비스 거부 공격



암호화하지 않은 통신이기 때문에 도청이 가능해 통신 경로상에서 <u>패킷</u>을 수집해 다른 사람이 메세지의 의미 파악이 가능하다.

- Packet은 정보를 보낼 때 특정 형태를 맞추어 보내는것



정보의 정확성 즉 완전성을 보장할 수 없어 변조가 가능하다.

- HTTP 통신을 통해 수신한 내용이 송신 측에서 보낸 내용과 일치한다고 보장이 불가능 하다.

이렇게 <u>HTTP는 보안 상의 문제로 실제 운용되는 사이트에서는 지양된다.</u>

# HTTP Header

클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있게 해준다.

------

**대표적인 항목**

## General Header ( 공통 헤더 )

- Date

```java
Date: (day-name), (day) (month) (year) (hour):(minute):(econd) GMT
```

ex)

“Date: Wed, 21 Oct 2015 07:28:00 GMT”

- Connection
  - Connection: clos : 메세지 교환 후 TCP 연결 종료
  - Connection: Keep-Alive : 메세지 교환 후 TCP 연결 유지
    - TCP : 전송 제어 프로토콜로 두 개의 호스트를 연결하고 데이터 스트림을 교환하게 해주는 핵심 네트워크 프로토콜

------

## Request Header ( 요청 헤더 )

- Host : 요청하는 자의 호스트명, 포트 번호를 포함하고 있다.

```java
Host: developer.mozilla.org
```

- User-Agent : 요청자의 소프트웨어 정보를 표현한다.

  - — 소프트웨어 정보: os, 브라우저, 기타버전 정보

  ```java
  User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
  ```

  - Request에 넣지 않고 요청을 했을 경우 정보를 주지 않은 곳도 있다.

- Accept : 요청자가 원하는 미디어의 타입 및 우선 순위를 표현한다.

  - Accept-Language : 사용자가 원하는언어셋이다.
  - Accept-Encodig : 사용자가 원하는 인코딩 방식이다.

  ```java
  Accept: application/json, text/plain,
  -> json > text > all type 순으로 받는다는 표현이다.
  Accept-Language: en-US,en;q=0.5
  -> 언어는 en이라는 표현이다. q는 가중치다.
  Accept-Encoding: gzip, deflate, br
  -> gzip, deflate, br(Brotli) 등등의 압축 포맷을 받는다는 표현이다.
  ```

- cookie : 서버에 의해 이전에 저장된 쿠키를 포함시키는 속성

- Referer : 현재 요청을 보낸 페이지의 절대 혹은 부분 주소를 포함한다.

  - referer-policy : 요청과 함께 얼마나 많은 레퍼럴 정보를 포함하는지 알려준다.
  - referer-after : 응답 헤더에 속하는 것이고 다음에 올 요청이 이루어지기 전에 사용자가 대기해야 하는 시간을 가르킨다.

- Authorization : 인증토큰(JWT,Bearer)을 서버로 보낼 때 사용한다.

  - API요청 같은 것을 할 때 토큰이 없으면 거절당하기 때문에 이 때 사용하면 된다.

```java
Authorization: Bearer XXXXXXXXXXXXX
```

보통 Basic이나 Bearer같은 토큰의 종류를 먼저 알리고 그 다음에 실제 토큰 문자를 적어 보낸다.

------

## Reaponse Header ( 응답 헤더 )

- Server : 서버 소프트웨어의 정보를 표현
- content-encoding : 응답하는 내용의 인코딩 포맷을 표현
- content-type : 응답하는 내용의 타입과 문자 포맷을 표현
- cache-control : 캐시 관리에 대한 정보를 표현

```java
ex) cache-control :
no-cache(서버측에 캐시를 사용해도 되는지 확인),
no-store(캐싱x),
must-revalidate(만료 캐시만 서버측에 확인),
public(중개 서버에 저장 가능)/private(사용자 브라우저에만 등록),
max-age(캐시 유효기간)
```

- date : 응답 메세지가 생성된 시간을 표현
- vary : 캐시된 응답을 향후의 응답에 사용할 기준을 표현

```java
ex) Vary: User-Agent
이렇게 설정되어 있으면, 모바일 유저에게 데스크탑 유저를 위한 캐시 컨텐츠가 제공되지 않게 할 수 있다.
```

- Set-Cookie : 서버에서 사용자에게 세션쿠키 정보를 전달
- Age : max-age내에서 캐시가 얼마나 지났는지 초 단위로 표현한다.
  - max-age : 캐시의 수명을 결정하는 정책
