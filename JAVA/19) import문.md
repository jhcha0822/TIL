# import문

소스코드를 작성할 때 다른 패키지의 클래스를 사용하려면 패키지명이 포함된 클래스 이름을 사용해야 한다. 하지만 매번 패키지명을 붙어 작성하기란 상당히 귀찮다.

클래스의 코드를 작성하기 전에 `import`문으로 사용하고자 하는 클래스의 패키지를 미리 명시해주면 소스코드에 사용되는 클래스이름에서 패키지는 생략할 수 있다.

`import`문의 역할은 **컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 것이다.** 컴파일 시에 컴파일러는 `import`문을 통해 소스파일에 사용된 클래스들의 패키지를 알아 낸 다음, 모든 클래스이름 앞에 패키지명을 붙여 준다.

특히 Eclipse의 경우, `ctrl+shift+o`를 누르면 자동으로 `import`문을 추가해주는 편리한 기능이 있다.

### import문의 선언

모든 소스파일(.java)에서 `import`문은 `package`문 다음에, 그리고 클래스 선언문 이전에 위치해야 한다. `import`문은 `package`문과 달리 한 소스파일에 여러 번 선언할 수 있다. 즉, 여러 클래스를 받아올 수 있다.

```java
import 패키지명.클래스명;
// 또는
import 패키지명.*; // 같은 패키지에 여러개의 클래스를 사용할 때
```
후자의 경우에는 지정된 패키지에 속하는 모든 클래스를 패키지명 없이 사용할 수 있다. 하지만 `import`하는 패키지의 수가 많을 때 어느 클래스가 어느 패키지에 속하는지 구별하기 어렵고, **하위 패키지의 클래스까지 포함하는 것이 아니라는 것에 주의한다.**

```java
import java.util.*;
import java.text.*;
```
```java
import java.*;
```
**전자를 후자로 대체할 수 없다.**

지금까지 `System`과 `String`같은 `java.lang`패키지의 클래스들을 패키지명 없이 사용할 수 있었던 이유는 모든 소스파일에는 묵시적으로 다음과 같은 `import`문이 선언되어 있기 때문이다.

```java
import java.lang.*;
```

### static import문

`import`문을 사용하면 클래스의 패키지명을 생략할 수 있는 것과 같이, `static import`문을 사용하면 `static`멤버들을 호출할 때 클래스 이름을 생략할 수 있다. 특정 클래스의 `static`멤버 호출이 잦을 때 유용하다.

```java
import static java.lang.Integer.*; // Integer클래스의 모든 static 메서드
import static java.lang.Math.random; // Math.random()만, 괄호 없음에 주의
import static java.lang.System.out; // System.out을 out만으로 참조가능
```

```java
//위 import문의 효과
out.println(random()); // System.out.println(Math.random());와 같음
```