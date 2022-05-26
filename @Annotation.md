# @Annotation

Annotation : 클래스와 메소드에 추가하여 다양한 기능을 부여하는 역할



## 어노테이션 종류

`@Component` : 개발자가 생성한 Class를 Spring의 Bean으로 등록할 때 사용하는 것.

`@ComponentScan` : Spring Framework는 @Component, @Service, @Repository, @Controller, @Configuration 중 1개라도 등록된 클래스를 찾으면 Context에 Bean으로 등록한다.

- @ComponnentScan Annotation이 있는 하위클래스의 하위 Bean을 등록 될 클래스들을 스캔하여 Bean으로 등록해준다.

`@Bean` : 개발자가 제어 불가능한 외부 라이브러리와 같은 것들을 Bean으로 만들 때 사용

`@Controller` : Spring에게 해당 Class가 Controller의 역할을 한다고 명시하기 위해 사용 

`@RequestHeader` : Request의 header값을 가져올 수 있으며 해당 어노테이션을 쓴 메소드의 파라미터에 사용