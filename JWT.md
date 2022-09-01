# JWT

JSON Web Token으로 인증에 필요한 정보들을 암호화시킨 토큰

------

![image](https://user-images.githubusercontent.com/103401813/171411704-03a8c97d-261b-49bf-98b5-fa46868ad5b7.png)

## JWT 기반 인증

JWT 토큰(Access Token)을 HTTP 헤더에 실어 서버가 클라이언트를 식별하는 방식

- URL의 파라미터로도 전달 가능

**토큰 기반 인증 시스템**

클라이언트가 서버에 접속을 하면 서버에서 해당 **클라이언트에게 인증되었다는 의미로 토큰을 부여**한다.

→ 토큰은 유일하고 클라이언트는 서버에 요청을 보낼 때 요청 헤더에 토큰을 심어서 보낸다.

- 서버에서 클라이언트로 받은 토큰을 서버에서 제공한 토큰과의 일치여부를 체크하여 인증과정을 처리하게 된다.

![img](https://user-images.githubusercontent.com/103401813/171411936-5ec02ebb-4da9-4e77-b7b3-f054c6d88d69.png)

------

## JWT 구조

![img](https://user-images.githubusercontent.com/103401813/171412002-29d6432f-d6b0-4901-b8df-789527067d43.png)

JWT는 **.(점)**을 구분자로 나누어지는 세 가지 문자열의 조합

- JWT토큰을 만들 때 담당 라이브러리가 자동으로 인코딩(코드화, 암호화)과 해싱 작업(원본 문자열을 알아볼 수 없는 난해한 문자열로 정의(표현) 하는 과정)을 해준다.

**실제 디코딩된 JWT의 구조**

- decoding(디코딩) : 변형된 형태로 저장된 파일을 원래 상태로 되돌리는 것

------

## **Header ( 알고리즘 형식 RSA / SHA256 등 )**

- typ : 토큰(JWT)의 타입을 지정

- alg : Signature(전자 서명)해싱 알고리즘을 지정한다. 보통 HMAC SHA256 또는 RSA가 사용되고 알고리즘은 토큰을 검증할 때 사용되는 signature 부분에서 사용된다.

- kid : 서명 시 사용하는 키(Public/Private Key)를 식별하는 값

  → 서명 암호화 알고리즘

  위와 같은 JSON 객체를 문자열로 직렬화하고 UTF-8과 Base64 URL-Safe로 인코딩하면 다음과 같이 인코딩(암호화, 코드화)이 완료된다.

  ```markdown
  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
  ```

------

## Payload ( 정보 )

토큰에서 사용할 정보의 조각들인 Claim(클레임)이라고 부르고 이는 Json(Key/Value)형태의 한 쌍으로 이루어져 있다.

→ 서버와 클라이언트가 주고받는 시스템에서 실제로 사용될 정보에 대한 내용을 담고 있다.

- 클레임 : 실제 JWT를 통해서 알 수 있는 데이터
- 토큰에는 여러개의 클레임을 넣을 수 있다.

**클레임의 종류**

- Registered Claim ( 등록된 클레임 )
- Public Claim ( 공개 클레임 )
- Private Claim ( 비공개 클레임 )

### Registered Claim ( 등록된 클레임 )

토큰에 대한 정보들을 담기위하여 이름이 이미 정해진 클레임

등록된 클레임의 사용은 모두 optional( 선택적 )이다.


이에 포함된 클레임 이름

- iss
  - 토큰 발급자 ( issuer )
- sub
  - 토큰 제목 ( subject )
- aud
  - 토큰 대상자 ( audienece )
- exp
  - 토큰의 만료시간 ( expiraton )
  - 시간은 NumericDate 형식으로 되어 있어야 하며 ( ex : 1480849147370 )언제나 현재 시간보다 이후로 설정되어 있어야한다.
- nbf
  - Not Before을 의미하고 토큰의 활성 날짜와 비슷한 개념이다.
  - NumericDate형식으로 날짜를 지정하며 이 날짜가 지나기 전까지는 토큰이 처리되지 않는다.
- iat
  - 토큰이 발급된 시간( issued at )
  - 이 값을 사용하여 토큰의 age가 얼마나 되었는지 판단 가능하다
- jti (JWI ID)
  - JWT의 고유 식별자로 주로 중복적인 처리를 방지하기 위하여 사용된다.
  - 일회용 토큰에 사용하면 유용하다.

→ 필수는 아니지만 exp, iat, jti는 꼭 claims에 넣어줘야 좋다.

### Public Claim ( 공개 클레임 )

충돌이 방지된 (collision-resistant)이름을 가지고 있어야 한다.

- 충돌을 방지하기 위해서 클레임 이름을 URI 형식으로 짓는다.


### Private Claim ( 비공개 클레임 )

등록된 클레임이 아니고 공개된 클레임도 아니다.

양 측간에 ( 보통 클라이언트 ↔ 서버 ) 협의하에 사용되는 클레임 이름들이다. 공개 클레임과는 달리 이름이 중복되어 충돌이 될 수 있으니 사용할 때에 유의해야 한다.

단 위 정보를 payload객체에 담아둘 경우  **패스워드  혹은 민감한 정보를 절대로 담아두어서는 안된다.**

## Signature ( 서명 )

토큰을 인코딩하거나 유효성 검증을 할 때 사용하는 고유한 암호화 코드

- 서명은 헤더와 페이로드의 값을 각각 BASE64로 인코딩하고 인코딩한 값을 비밀 키를 이용해 헤더에서 정의한 알고리즘으로 해싱을하고 이 값을 다시 BASE64로 인코딩하여 생성한다.
  - 해싱 : 원본 문자열을 알아볼 수 없는 난해한 문자열로 정의하는 과정
    - 키(Key) 값을 해시 함수(키 값을 값(Value)이 저장되는 주소 값으로 바꾸기 위한 수식)라는 수식에 대입시켜 계산한 후 나온 결과를 주소로 사용하여 바로 값에 접근하게 하는 방법
→ 헤더의 인코딩 값과 정보의 인코딩 값을 합친 후 비밀키로 해쉬(다양한 길이를 가진 데이터를 고정된 길이를 가진 데이터로 매핑한 값)하여 생성한다.
![img](https://user-images.githubusercontent.com/103401813/171412849-82ab0db6-035e-47c3-9071-b98cf2c820a4.png)
시그니처에서 사용하는 알고리즘은 헤더에서 정의한 알고리즘 방식을 활용한다.
구조는 (헤더+페이로드)와 서버가 갖고 있는 유일한 key값을 합친 것을 헤더에서 정의한 알고리즘으로 암호화 한다.
![img](https://user-images.githubusercontent.com/103401813/171413057-81c6b8b6-f8ff-4001-9ba8-e627357e300a.png)

Signature은 서버 측에서 관리하는 비밀키가 유출되지 않는 이상 복호화 할 수 없다.
→ 토큰의 위변조 여부를 확인하는데 사용한다.

------

## JWT 토큰 예시

![download](https://user-images.githubusercontent.com/103401813/171413505-eb8f42fe-bfbb-452c-9443-6343b2f9e5fb.jpg)

생성된 토큰은 HTTP 통신을 할 때 Authorization이라는 key의 value로 사용된다.

일반 적으로 value에는 Beare가 앞에 붙여진다.

```markdown
{ 
 "Authorization": "Bearer {생성된 토큰 값}",
}
```

## JWT 인코드/디코드 온라인 사이트
https://jwt.io/
![Untitled-4-950x767](https://user-images.githubusercontent.com/103401813/171413885-fa66c737-9591-4e90-add1-4074c4f9482c.png)

하단의 텍스트가 파란색으로 Signature Verified라고 뜨면 JWT토큰이 검증되었다는 것이다.

## JWT를 통한 인증 과정
![img](https://user-images.githubusercontent.com/103401813/171414843-ca21a8a5-9178-4357-9ba1-2202aeb6f2aa.png)
