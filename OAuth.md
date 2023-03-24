구글, 페이스북과 같은 **다양한 플랫폼의 특정한 사용자 데이터에 접근**하기 위해 `제3자 클라이언트`(본인의 서비스)가 **사용자의 접근 권한을 위임**받을 수 있는 표준 프로토콜

------

## OAuth 사용이유

다른 서비스에 우리 서비스를 이용중 인 사용자의 정보를 넘겨주는 것은 부담이 심하고 정보 유출의 가능성도 있기 때문에 다양한 회사들은 자신들만의 방법으로 이런 문제를 해결했지만 결국 특정 서비스와 연동하는 서비스를 만들기 위해 OAuth가 등장하게 되었다.

------

## OAuth 1.0

**3-legged-auth**

- user
- consumer
- service provider

OAuth 1.0은 구현이 복잡하고 웹이 아닌 어플리케이션에서의 지원이 부족해 HMAC을 통해 암호화를 하는 번거로운 과정이 있었다. 또한 인증 토큰이 만료되지 않는다는 문제점도 있었다.

이후 이런 단점을 보안한 OAuth 1.0a 버전이 나왔지만 모바일 어플리케이션 등에서의 안전하게 사용될 수 없는 사례가 존재했다.

------

## OAuth 2.0

**OAuth 참여자**

**Resource Server**: Cilent가 제어하고자 하는 `자원을 보유`하고 있는 서버

→ 페이스북, 구글 등

**Resource Owner**: 자원의 `소유자`

→ Client가 제공하는 서비스를 통해 로그인하는 실제 유저

**Client**: Resoure Server에 접속해서 `정보를 가져오고자` 하는 클라이언트

- 내 서버가 Client가 되는 이유는?

  조금만 다르게 생각하면 바로 알아챌 수 있을 것 같다. 내 서버는 현재 구글이나 페이스북 같은 Resource Server에 자원을 요청하는 입장이기 때문에 Client입장이 되는 것이다. 👍

## OAuth 동작과정

**Clinet 등록**

OAuth 2.0 사용 전에 Client를 Resource Server에 등록을 시켜야 한다. 이때 Redirect URI 등록을 해야 한다.

Redirect URI는 사용자가 OAuth 2.0 서비스에서 인증을 마치고 사용자를 리디렉션 시킬 위치이다.

- **Redirect URI란?**

  > OAuth 2.0 서비스는 인증이 성공한 사용자를 사전에 등록된 Redirect URI로만 리디렉션 시킨다. 승인되지 않은 URI로 리디렉션 될 경우 Authirization Code를 중간에 탈취당할 위험성이 있기 때문에 일부 OAuth 2.0 서비스는 여러 Redirect URI를 등록할 수 있다.

  Redirect URIsms 기본적으로 보안을 위해 `https`만 허용된다. 루프백(localhost)은 `예외적으로 http`가 허용된다.