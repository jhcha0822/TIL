# super

`super`는 자식 클래스에서 부모 클래스로부터 상속받은 멤버를 참조하는데 사용되는 참조변수이다. 멤버변수와 지역변수의 이름이 같을 때 `this`를 붙여서 구별했듯이, 상속받은 멤버와 자신의 멤버와 이름이 같을 때에는 `super`를 붙여서 구별할 수 있다.

부모 클래스로부터 상속받은 멤버도 자식 클래스 자신의 멤버이므로 `super`대신 `this`를 사용할 수 있다. 그래도 부모 클래스의 멤버와 자식 클래스의 멤버가 중복 정의되어 서로 구별해야하는 경우에만 `super`를 사용하는 것이 좋다.

부모의 멤버와 자신의 멤버를 구별하는데 사용된다는 점을 제외하고는 `super`와 `this`는 근본적으로 같다. 모든 인스턴스메서드에는 자신이 속한 인스턴스의 주소가 지역변수로 저장되는데, 이것이 참조변수인 `this`와 `super`의 값이 된다.

`static`메서드(클래스 메서드)는 인스턴스가 관련이 없다. 그래서 `this`와 마찬가지로 `super`역시 `static`메서드에서는 사용할 수 없고 인스턴스 메서드에서만 사용할 수 있다.

```java
class SuperTest {
    public static void main(String[] args) {
        Child c = new Child();
        c.method();
    }
}

class Parent {
    int x=10;
}

class Child extends Parent {
    void method() {
        System.out.println("x=" + x);
        System.out.println("this.x=" + this.x);
        System.out.println("super.x=" + super.x);
    }
}
```
> 실행 결과:
> x=10
> this.x=10
> super.x=10

위 코드의 경우, `x`, `this.x`, `super.x` 모두 같은 변수를 의미하므로 모두 같은 값이 출력되었다.

```java
class SuperTest2 {
    public static void main(String[] args) {
        Child c = new Child();
        c.method();
    }
}

class Parent {
    int x=10;
}

class Child extends Parent {
    int x=20;
    void method() {
        System.out.println("x=" + x);
        System.out.println("this.x" + this.x);
        System.out.println("super.x" + super.x);
    }
}
```
> 실행 결과:
> x=20
> this.x=20
> super.x=10

<<<<<<< HEAD
같은 이름의 멤버변수가 부모 클래스인 `Parent`에도 있고, 자식 클래스 `Child`에도 있을 때에는 `super.x`와 `this.x`가 서로 다른 값을 참조하게 된다. `super.x`는 부모 클래스로부터 상속받은 멤버변수 `x`를 뜻하며, `this.x`는 자식 클래스에 선언된 멤버변수를 뜻한다.

> 이처럼 부모 클래스에 선언된 멤버변수와 같은 이름의 멤버변수를 자식 클래스에서 중복해서 정의하는 것이 가능하며 참조변수 `super`를 이용해서 서로 구별할 수 있다.

변수만이 아니라 메서드 역시 `super`를 써서 호출할 수 있다. 특히 부모 클래스의 메서드를 자손 클래스에서 **오버라이딩**한 경우에 `super`를 사용한다.

```java
class Point {
    int x;
    int y;
    String getLocation() {
        return "x: " + x + ", y: " + y;
    }
}

class Point3D extends Point {
    int z;
    String getLocation() { // 오버라이딩
        // return "x: " + x + ", y: " + y + ", z:" + z;
        return super.getLocation() + ", z: " + z; // 부모의 메서드 호출
    }
}
```
`getLocation()`을 오버라이딩할 때 부모 클래스의 `getLocation()`을 호출하는 코드를 포함시켰다. 부모클래스의 메서드의 내용에 추가적으로 작업을 덧붙이는 경우라면 이처럼 `super`를 포함하여 부모클래스의 메서드를 포함시키는 것이 이득이다. 후에 부모클래스의 메서드가 변경되더라도 변경된 내용이 자식클래스의 메서드에 자동적으로 반영될 것이기 때문이다.
=======
>>>>>>> 0963e64b480fe8ca18d929ebeafe7606dc512127
