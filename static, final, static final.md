# static, final, static final

## static(정적 변수, 클래스 변수)

클래스 내부에 선언하고 변수, 메소드의 키워드로 사용

- 프로그램이 실행되어 메모리에 올라갔을 때 단 한번만 메모리 공간이 할당된다.

= 인스턴스(실제 존재하는 객체)들이 공통적으로 같은 값이 유지되어야 할 때 사용

- 메모리에 고정적으로 할당되어 프로그램이 종료될 때 해제된다.
- 객체를 생성하지 않고도 변수나 함수 사용 가능

**메소드(Method)**

클래스 내부에 정의되어 어떠한 특정 작업을 수행하기 위한 명령문의 집합

- 클래스 : 객체를 만들어 내기 위한 틀, 객체와 관련된 변수와 메소드의 집합

객체 선언

Class 타입 변수명 = new 생성자

필드 선언

- 생성자와 메소드 중괄호 내부에 선언될 수 없다

<aside> 👉 타입 필드 [ = 초기 값]; ex) int a = 300;

</aside>

- 초기 값 설S정을 안 할 시 기본 값으로 정해진다.

### static 필드 사용 예시

```java
class Number{
    static int num = 0; //클래스 필드
    int num2 = 0; //인스턴스 필드
}

public class Static_ex {
	
    public static void main(String[] args) {
    	Number number1 = new Number(); //첫번째 number
    	Number number2 = new Number(); //두번쨰 number
    	
    	number1.num++; //클래스 필드 num을 1증가시킴
    	number1.num2++; //인스턴스 필드 num을 1증가시킴
    	System.out.println(number2.num); //두번째 number의 클래스 필드 출력
    	System.out.println(number2.num2); //두번째 number의 인스턴스 필드 출력
    }
}
```

출력

1 0

### static 메소드 사용

```java
class Name{
    static void print() { //클래스 메소드
	System.out.println("내 이름은 홍길동입니다.");
    }

    void print2() { //인스턴스 메소드
	System.out.println("내 학번은 1204입니다.");
    }
}

public class Static_ex {
	
    public static void main(String[] args) {
        Name.print(); //인스턴스를 생성하지 않아도 호출이 가능
    	
        Name name = new Name(); //인스턴스 생성
        name.print2(); //인스턴스를 생성하여야만 호출이 가능
    }
}
```

출력

내 이름은 홍길동입니다.

내 이름은 1204입니다.

- 정적 메소드는 클래스가 메모리에 올라갈 때 정적 메소드가 자동적으로 생성

## final(상수)

변수, 메소드, 클래스에 사용이 가능하고 선언 후 변경이나 수정이 불가능하다.

### final 변수

final을 붙인 변수는 더 이상 변수의 값을 수정할 수 없습니다.

```java
public class Service {

  public void variableFinal() {

    final int value = 2;  //final 변수 선언과 동시에 초기화 핗
}
```

수정이 불가능하여 **값의 관리**가 정확해집니다.

### final 객체

```java
final ArrayList<String> LIST = new ArraryList<String>();

LIST.add("A");
LIST.add("B");
```

Pet의 값을 고치기가 가능합니다.

왜냐하면 final LIST는 ArrayList의 값을 가진 것이 아니라 객체의 주소를 참조하고 있는 것이기 때문입니다.

**final로 선언된 객체는 new를 사용하여 다시 정의 할 수 없습니다.**

```java
LIST = new ArrayList<String>(); // 컴파일 오류 발생
```

### final 메소드

**자바 상속**

부모 클래스(상위 클래스)와 자식 클래스(하위 클래스)가 있으며 자식 클래스는 부모 클래스를 선택해서, 그 부모의 멤버를 상속받아 그대로 쓸 수 있게 된다.

- 단, 부모 클래스의 접근 제한을 갖는 필드 및 메소드는 자식이 물려받을 수 없다

**상속방법**

```java
public Class Parent{ .... }; // 부모 클래스
public Class Child extends parent { .... }; // 자식 클
```

**final 메소드는 Override(재정의)를 할 수 없다.**

```java
class Parent{

public final void aaa() {

System.out.println("aaa");

	}

}

class Child extends Parent{

@Override

public void aaa() {

   => Cannot override the final method from FinalParent

  // 해당 메소드는 오버라이딩이 인된다.

System.out.println("AAA");

	}

}
```

### final 클래스

final이 붙은 클래스 상속이 불가능하게 만듭니다.

```java
final class FinalParent{

	public void aaa() {

	System.out.println("aaa");

	}

}

class Child extends FinalParent{
=> The type FinalChild cannot subclass the final class FinalParent
// 클래스를 상속할 수 없다.

@Override

	public void aaa() {
	System.out.println("AAA");

	}

}
```

### static final(상수)

객체마다 저장되지 않고 클래스에만 포함되어 한 번 초기값이 저장되면 변경할 수 없다.

```java
public class UsedStaticFinal { 
	// 상수 선언 static final double INCH = 2.54;
	static final double CM = 1;
	static final double MONITOR_WIDTH;

	// 상수 초기값 선언
	static { 
		MONITOR_WIDTH = 14 * INCH * CM; 
	}

	// 상수 사용
	public static void main(String[] args) {
		System.out.println("14인치 모니터 cm는? "+ MONITOR_WIDTH); 
	} 
}
```

출력

14인치 모니터  cm는? 35.56