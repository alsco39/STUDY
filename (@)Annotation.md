# (@)Annotation

**Annotation(어노테이션)**

- **자바에서 코드 사이에 주석처럼 쓰이며 특별한 의미, 기능을 수행하도록 하는 기술**

  ![화면 캡처 2022-05-31 081645.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d806963-ab3a-46d7-a60e-87f5d0e63fa8/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2022-05-31_081645.png)

  - 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보를 제공
  - 소프트웨어 개발 툴이 빌드나 배치시 코드를 자동으로 생성할 수 있도록 정보를 제공
  - 런타임(실행)시 특정 기능을 실행하도록 정보를 제공

## 종류

- **@SpringBootApplication**

  @Configuration + @EnableAutoConfiguration + @ComponentScan 으로 주로 메인 클래스 위에서 사용된다.

  

- **@ResponseStatus**

  

  Spring MVC에서 HTTP 응답의 상태 코드를 설정할 때 사용한다.

  끝 점이 성공적으로 반환되면 Spring은 HTTP 200 (OK)  응답을 반환한다.

  - **컨트롤러의 메소드의 응답 상태**를 지정하려면 해당 메소드를 @ResponseStatus로 표시 가능하다.

  - 원하는 응답 상태에 대해 두 개의 상호 교환 가능한 인수 인 코드 및 값이 있다.

    ex) 쿠키이기 때문에 서버는 쿠키굽기 거부함을 나타낼 수 있다.

  - Spring은 표시된 메소드가 성공적으로 완료 될 때만 @Response을 사용한다.

- **@RequestMapping**

  특정 URI로 요청을 보내면 Controller에서 어떠한 방식으로 처리할지 정의를 한다. 이때 들어온 요청을 특정 메소드와 매핑하기 위해 사용하는 것이다.

  ```java
  @RequestMapping(value = "/getList",method = { RequestMethod.POST})
  ```

  **@GetMapping**

  GET 요청 방식의 API를 만들때 사용한다.

  ```java
  @GetMapping("/search") // /post/search
  ```

  **@DeleteMapping**

  ```java
  @DeleteMapping("/{postId}") 
      public void deletePost(@PathVariable int postId) {
          postService.deletePost(postId);
      }
  ```

  postId로 데이터를 찾아서 삭제(기존의 정보를 삭제할 때 주로 사용)

  요청시  Body값과 Content-Type값이 비워져 있다.

  - Content-Type : 클라이언트에게 반환된 컨텐츠의 컨텐프 유형이 무엇인지 알려준다

  URL을 통해 어떠한 데이터를 삭제할지 파라미터를 받는다.

  데이터 삭제에 성공한다면Body 값 없이 성공 응답만 보내게 된다.

  - Body : 해당 request의 실제 메세지,내용. Body가 없는 응답도 많다(GET 응답은 대부분 body가 없는 경우가 많다)

  **@PatchMapping**

  ```java
  @PatchMapping("/{postId}")
  ```

  리소스(사용될 수 있는 어떤 항목)의 일부분을 수정

  Patch는 **정보의 일부분이 변경**되는 방법이다.

- **@Getter**

  Getter 메소드를 생성해 준다

  객체 지향 프로그래밍에서는 객체의 데이터는 객체 외부에서 직접적으로 접근하는 것을 막는다. = 객체의 무결성

  → 메소드를 통해 데이터를 변경하는 방법 선호

  객체 외부에서 객체 필드 값을 사용하기 부적절한 경우에 메소드로 필드값을 가공 후, 외부로 전달

  → 이런 역할을 @Getter이 한다.

- **@Entity**

  @Entity 어노테이션이 붙은 클래스는 JPA(JAVA에서 제공하는 API)가 관리하는 클래스를 말한다.

  → 해당 클래스를 엔티티(테이블에 대응하는 하나의 클래스)라고 한다.

  - JPA를 사용해서 테이블과 매핑할 클래스는 반드시 @Entity어노테이션을 붙여야 한다.