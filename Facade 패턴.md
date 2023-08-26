## 퍼사드(Facade) 패턴

복잡한 서브 시스템을 인터페이스로 감싸서 사용하기 쉽게 만드는 것

⇒ 서브시스템을 더 쉽게 사용할 수 있도록 만드는 더 높은 수준의 인터페이스

- 구조 패턴 (클래스나 객체를 조합하여 더 큰 구조를 만드는 패턴) 에 해당

1. Facade : 클라이언트의 요청을 적절한 서브시스템 클래스에 위임한다.
2. Subsystem classes : facade에 대한 정보를 가지지 않고, 서비시스템 기능을 구현한다. 서브시스템 클래스는 facade에 의해서만 사용된다.
3. Client : facade에게 특정 행동을 수행해달라고 요청한다.

**특징**

**낮은 결합도** : 클라이언트가 서브시스템의 코드를 모르더라도 facade 클래스를 통해 사용 가능

**서브클래스를 직접 접근 가능** : facade 클래스를 통해 서브클래스를 사용할지 서브클래스를 직접 사용할지 선택 가능

**Facade**

GoOffice 클래스

```java
public class GoOffice {

    public void goToWork() {
        Wash wash = new Wash();

        wash.brushTeeth();
        wash.shower();
    }
}
```

**Subsystem**

Wash 클래스

```java
public class Wash {

    public void brushTeeth() {
        System.out.println("Brush my teeth");
    }

    public void shower() {
        System.out.println("Take a shower");
    }
}
```

**Client** 클래스

```java
public class Client {

    public static void main(String[] args) {
        GoOffice goOffice = new GoOffice();
        goOffice.goToWork();
    }
}
```

[ 실행결과 ]

Brush my teeth

Take a shower
