# super()

`this()`와 마찬가지로 `super()` 역시 생성자이다. `this()`는 같은 클래스의 다른 생성자를 호출하는데 사용되지만, `super()` 부모 클래스의 생성자를 호출하는데 사용된다.

자식 클래스의 인스턴스를 생성하면, 자식의 멤버와 부모의 멤버가 모두 합쳐진 하나의 인스턴스가 생성된다. 그래서 자식 클래스의 인스턴스가 부모 클래스의 멤버들을 사용할 수 있는 것이다. 이 때 부모 클래스 멤버의 초기화 작업이 수행되어야 하기 때문에 자식 클래스의 생성자에서 부모 클래스의 생성자가 호출되어야 한다.

생성자의 첫 줄에서 부모 클래스의 생성자를 호출해야 하는 이유는 자식 클래스의 멤버가 부모 클래스의 멤버를 사용할 수도 있으므로 부모의 멤버들이 먼저 초기화되어 있어야 하기 때문이다.

이와 같은 부모 클래스 생성자의 호출은 클래스의 상속관계를 거슬러 올라가면서 계속 반복된다. 마지막으로 모든 클래스의 최고 조상인 `Object`클래스의 생성자인 `Object()`까지 가서야 끝이 난다.

그래서 `Object`클래스를 제외한 모든 클래스의 생성자는 첫 줄에 반드시 자신의 다른 생성자 또는 부모의 생성자를 호출해야 한다. 그렇지 않으면 컴파일러는 생성자의 첫 줄에 `super();`를 자동적으로 추가할 것이다.

> `Object`클래스를 제외한 모든 클래스의 생성자 첫 줄에 생성자, `this()` 또는 `super()`를 호출해야 한다. 그렇지 않다면 컴파일러가 자동적으로 `super();`를 생성자의 첫 줄에 삽입한다.

인스턴스를 생성할 때에는 클래스를 선택하는 것만큼 생성자를 선택하는 것도 중요한다.

    1. 클래스 - 어떤 클래스의 인스턴스를 생성할 것인가?
    2. 생성자 - 선택한 클래스의 어떤 생성자를 이용해서 인스턴스를 생성할 것인가?

```java
class PointTest {
    public static void main(String[] args) {
        Point3D p3 = new Point3D(1, 2, 3);
    }
}

class Point {
    int x, y;
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    String getLocation() {
        return "x: " + x + ", y: " + y;
    }
}

class Point3D extends Point {
    int z;
    Point3D(int x, int y, int z) {
        // super();
        this.x = x;
        this.y = y;
        this.z = z;
    }
    String getLocation() { // 오버라이딩
        return "x: " + x + ", y: " + y + ", z: " + z;
    }
}
```
`Point3D()` 생성자 첫 줄에서 다른 생성자를 호출하지 않기 때문에 컴파일러가 `super();`를 여기에 삽입한다. `super()`는 `Point3D`의 조상인 `Point`클래스의 기본 생성자인 `Point()`를 의미한다.

`Point3D`클래스의 인스턴스를 생성하면, 생성자 `Point3D(int x, int y, int z)`가 호출되면서 첫 문장인 `super();`를 수행하게 된다. `super()`는 `Point3D`클래스의 조상인 `Point`클래스의 기본 생성자인 `Point()`를 뜻하므로 `Point()`가 호출된다.

그러나 `Point`클래스에 `Point()`가 정의되어 있지 않기 때문에 컴파일 에러가 발생한다. 이 에러를 수정하려면, `Point`클래스에 생성자 `Point()`를 추가해주던가, 생성자 `Point3D(int x, int y, int z)`의 첫 줄에서 `Point(int x, int y)`를 호출하도록 변경하면 된다.

> 생성자가 정의되어 있는 클래스에는 컴파일러가 기본 생성자를 자동적으로 추가하지 않는다.

```java
Point3D(int x, int y, int z) {
    super(x, y); // 부모클래스의 생성자 Point(int x, int y)를 호출
    this.z = z;
<<<<<<< HEAD
}
```
부모 클래스의 멤버변수는 이처럼 부모의 생성자에 의해 초기화되도록 한다.

=======
}
>>>>>>> 0963e64b480fe8ca18d929ebeafe7606dc512127
