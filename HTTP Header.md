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