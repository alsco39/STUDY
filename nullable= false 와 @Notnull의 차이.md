# nullable= false 와 @Notnull의 차이

------

## nullable = false

DDL에 생성 시 Not null 설정이 적용되어 테이블이 생성된다.

빈 문자열의 입력은 허용하지만 null값을 입력할 경우 DB insert하는 과정에서 에러가 발생한다.

- 유효성 검사에서 오류가 발생하지 않는다.
- null을 넣은 엔티티를 생성이 된 뒤 레포지토리에 전달 된 값이 DB에 넘어간 뒤에 예외가 발생 해 위험한 오류를 맞을 수 있다.

## @Notnull

DDL에서 Not null설정이 적용되어 테이블이 생성된다.

공백입력은 허용하지만 NULL입력은 유효성 검증과정에서 오류가 발생한다.

- 제약조건 설정과 유효성 검사를 같이 하기 때문에 좀 더 안전하게 사용할 수 있다.

DB에 SQL 쿼리를 보내기 전에 예외가 발생하기 때문에

JPA에서 레포지토리 인터페이스가 잘못된 엔티티를 저장할 때, ConstraintViolationException(제약 조건 위반)을 발생시킨다.

- @Valid, @Validated없이 엔티티를 검증가능하다
