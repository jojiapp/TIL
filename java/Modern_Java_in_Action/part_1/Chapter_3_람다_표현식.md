# Chapter 3. 람다 표현식

- [3.1 람다란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#31-람다란-무엇인가)
- [3.2 어디에, 어떻게 람다를 사용할까?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#32-어디에-어떻게-람다를-사용할까)
    - [3.2.1 함수형 인터페이스](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#321-함수형-인터페이스)
    - [3.2.2 함수 디스크립터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#322-함수-디스크립터)
- [3.3 람다 활용 : 실행 어라운드 패턴](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#33-람다-활용--실행-어라운드-패턴)
    - [3.3.1 1단계 : 동작 파라미터화를 기억하라](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#331-1단계--동작-파라미터화를-기억하라)
    - [3.3.2 2단계 : 함수형 인터페이스를 이용해서 동작 전달](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#332-2단계--함수형-인터페이스를-이용해서-동작-전달)
    - [3.3.3 3단계 : 동작 실행](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#333-3단계--동작-실행)
    - [3.3.4 4단계 : 람다 전달](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#334-4단계--람다-전달)
- [3.4 함수형 인터페이스 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#34-함수형-인터페이스-사용)
    - [3.4.1 Predicate](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#341-Predicate)
    - [3.4.2 Consumer](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#342-Consumer)
    - [3.4.3 Function](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#343-Function)
- [3.5 형식 검사, 형식 추론, 제약](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#35-형식-검사-형식-추론-제약)
    - [3.5.1 형식 검사](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#351-형식-검사)
    - [3.5.2 같은 람다, 다른 함수형 인터페이스](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#352-같은-람다-다른-함수형-인터페이스)
    - [3.5.3 형식 추론](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#353-형식-추론)

`익명 클래스`로 다양한 동작을 구현할 수 있지만, 너무 많은 코드가 필요하고 깔끔하지 않습니다. 깔끔하지 못한 코드는 `동작 파라미터`를 실전에 적용하는 것을 막는 요소가 됩니다.

`Java 8`에 생긴 `Lambda Expresstion`을 이용하면 `익명 클래스`처럼 메소드를 인수로 전달할 수 있습니다.

`Lambda`와 `메소드 참조`를 같이 사용하면 훨씬 간결하게 코드를 작성할 수 있습니다.

## 3.1 람다란 무엇인가?

`Lambda Expression`은 메소드로 전달할 수 있는 `익명 함수`를 단순화한 것이라고 할 수 있습니다.  
`Lambda Expression`은 이름은 없지만, `파라미터 리스트`, `바디`, `반환 형식`, `발생할 수 있는 예외 리스트`는 가질 수 있습니다.

`Lambda`는 다음과 같은 특징이 있습니다.

- `익명`: 이름이 없으므로 `익명`이라 표현합니다. 구현 할 코드가 줄어듭니다.
- `함수`: 특정 메소드에 종속적이지 않으므로 `함수`라고 부릅니다.
- `전달`: 메소드 인수로 전달하거나 변수로 저장할 수 있습니다.
- `간결성`: `익명 클래스`처럼 많은 코드를 구현할 필요가 없습니다.

> `Lambda`라는 용어는 **람다 미적분학** 학계에서 개발한 시스템에서 유래했습니다.

`Lambda`는 `Java 8` 이전에 할 수 없었던 일들을 제공하는 것이 아닙니다.  
다만, `동작 파라미터`를 이용할 때 `익명 클래스` 처럼 많은 코드를 작성할 필요가 없습니다.

결과적으로는 코드가 간결하고 유연해진다는 장점이 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Comparator<Apple> byWeight = new Comparator<Apple>() {
            @Override
            public int compare(Apple o1, Apple o2) {
                return o1.getWeight().compareTo(o2.getWeight());
            }
        };
    }
}
```

위의 기존 코드를 `Lambda`로 구현하면 아래와 같이 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Comparator<Apple> byWeight = (Apple o1, Apple o2) -> o1.getWeight().compareTo(o2.getWeight());
    }
}
```

- 파라미터 리스트 `(Apple o1, Apple o2)`: `Comparator`의 `compare` 메소드의 파라미터
- 화살표 `->`: 파라미터와 바디를 구분합니다.
- 람다 바디: 반환값에 해당하는 표현식입니다.

`Java` 설계자는 `C#`이나 `스칼라` 같은 비슷한 기능을 가진 다른 언어와 비슷한 문법을 `Java`에 적용하기로 했습니다.

`Lambda`의 기본 문법은 아래와 같습니다.

```text
(parameters) -> expression  // `바디`가 한줄 이면 `return` 키워드를 생략할 수 있습니다.
```

또는 아래 처럼 `{}`안에 작성할 수 있습니다.

```text
(parameters) -> { statements; } // 이 경우에는 return 을 명시적으로 적어주어야 합니다.
```

## 3.2 어디에, 어떻게 람다를 사용할까?

`Lambda`는 `함수형 인터페이스`에서 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        List<Apple> greenApples = filter(inventory, (Apple a) -> GREEN == a.getColor());
    }
}

```

위의 예제는 `filter` 메소드가 `함수형 인터페이스`인 `Predicate<T>`를 두 번째 인자로 받기 때문에, `Lambda`로 값을 넘겨준 것입니다.

### 3.2.1 함수형 인터페이스

`함수형 인터페이스`는 정확히 하나의 `추상 메소드`를 지정하는 `interface`입니다.

위의 예제에서 살펴 본 `Predicate<T>`는 `boolean test(T t)` 메소드 하나만 `추상 메소드`이기 떄문에 `함수형 인터페이스`입니다.

```java
public interface Predicate<T> {
    boolean test(T t);
}
```

```java
public interface Comparator<T> {
    int compare(T o1, T o2);
}
```

```java
public interface Runnable {
    void run();
}
```

```java
public interface ActionListener extends EventListener {
    void actionPerformed(ActionEvent e);
}
```

```java
public interface Callable<V> {
    V call() throws Exception;
}
```

```java
public interface PrivilegedAction<T> {
    T run();
}
```

위의 `interface`들은 하나의 `추상 메소드`만 가지므로 `함수형 인터페이스` 입니다.

> `default` 메소드가 있더라도, `추상 메소드`가 오직 하나면 함수형 인터페이스 입니다.

`함수형 인터페이스`를 `Lambda expresstion`으로 구현하여 사용할 수 있습니다. 그렇게 되면 기존 처럼 해당 `interface`를 상속받아 구현하거나, 지저분한 `익명 클래스`를 사용하지 않아도
됩니다.

### 3.2.2 함수 디스크립터

`함수형 인터페이스`의 `추상 메소드 시그니처`는 `Lambda expresstion`의 `시그니처`를 가리킵니다.

> `Lambda expression`의 `시그니처`를 서술하는 메소드를 `함수 디스크립터` 라고 부릅니다.

`() -> void`는 `파라미터 리스트`가 없고 `void`를 반환하는 함수를 의미합니다.  
`(Apple, Apple) -> int`는 `Apple`객체 두개를 전달 받아 `int`를 반환하는 함수를 의미합니다.

`Lambda expression`을 사용할 때, `바디`가 한 줄이라면 `{}`와 `return` 키워드를 생략할 수 있다고 했습니다.
`void`처럼 반환 값이 없는 `함수`도 `{}`를 생략하고 작성할수 있습니다.

#### @FunctionalInterface는 무엇인가?

`함수형 인터페이스`를 보면 `@FunctionalInteface`가 추가되어 있는걸 볼 수 있습니다.

해당 `어노테이션`이 붙어있으면 `함수형 인터페이스`라고 생각하고, 그에 맞지 않게 구현이 되면 컴파일 에러가 발생합니다.

`@Override`가 붙어있으면 `override`할 메소드와 `시그니처`가 다르면 컴파일 에러가 발생하는것과 비슷합니다.

## 3.3 람다 활용 : 실행 어라운드 패턴

`자원 처리`에 사용되는 `순환 패턴`은 자원을 열고, 처리하고, 자원를 닫는 순서로 이루어집니다.

`설정`과 `정리`과정은 대부분 비슷하므로 `실제 처리 코드`는 `설정`과 `정리`에 둘러 쌓인 형태를 갖습니다. 이러한 형식의 코드를 `실행 어라운드 패턴`이라고 합니다.

```java
class Foo {
    public String processFile() throws IOException {
        try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
            return br.readLine(); // 실제 처리 코드
        }
    }
}
```

`Java 7`에 추가된 `try-with-resources`구문을 사용하면 자원을 명시적으로 닫을 필요가 없으므로 조금 더 간결하게 작성이 가능합니다.

### 3.3.1 1단계 : 동작 파라미터화를 기억하라

현재 위의 코드는 한 번에 한줄만 읽는 코드지만 요구사항으로 한 번에 두 줄을 읽어야 하거니, 가장 자주 사용되는 단어를 반환해야 한다면 `실제 처리 코드`만 `변경`되면 됩니다.

`실제 처리 코드`를 `동작 파라미터화`한다면 유연하게 대처가 가능합니다.

### 3.3.2 2단계 : 함수형 인터페이스를 이용해서 동작 전달

우선, `processFile` 메소드에서 실행할 동작을 전달해야 합니다.

`BufferedReader -> String`과 `IOException`을 던질 수 있는 `시그니처`와 일치하는 `함수형 인터페이스`를 만들어야 합니다.

```java

@FunctionalInterface
public interface BufferedReaderProcessor {
    String process(BufferedReader b) throws IOException;
}
```

`processFile` 메소드의 인자로 `BufferedReaderProcessor`를 받을 수 있도록 `processFile` 메소드를 변경합니다.

```java
class Foo {
    public String processFile(BufferedReaderProcessor processor) throws IOException {
        ...
    }
}
```

### 3.3.3 3단계 : 동작 실행

`processFile`에서 전달 받은 동작을 실행 하도록 메소드를 변경합니다.

```java
class Foo {
    public String processFile(BufferedReaderProcessor processor) throws IOException {
        try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
            return processor.process(br); // 전달 받은 동작을 수행
        }
    }
}
```

### 3.3.4 4단계 : 람다 전달

이제 `Lambda`를 이용해서 원하는 동작을 `processFile` 메소드에 전달하면 됩니다.

```java
class Foo {
    public static void main(String[] args) {
        processFile(br -> br.readLine());
        processFile(br -> br.readLine() + br.readLine());
    }
}
```

> `Lambda`의 `파라미터 리스트`에서 타입을 지정해주지 않아도 `타입 추론`으로 타입이 지정되기 때문에 생략할 수 있습니다.

이제 변화하는 요구사항에 유연하게 대처할 수 있습니다.

## 3.4 함수형 인터페이스 사용

`함수형 인터페이스`의 `추상 메소드`는 `Lambda expression`의 `시그니처`를 묘사합니다.

> `함수형 인터페이스`의 `추상 메소드 시그니처`를 `함수 디스크립터`라고 합니다.

다양한 `Lambda expression`을 사용하려면 공통된 `함수 디스크립터`를 기술하는 `함수형 인터페이스 집합`이 필요합니다.

`Java 8`에서는 `java.util.function` 패키지로 여러 가지 새로운 `함수형 인터페이스`를 제공합니다.

### 3.4.1 Predicate

`java.util.function.Predicate<T>`는 제네릭 형식의 `T` 객체를 전달받아 `boolean` 타입을 반환 하는 `test` 추상 메소드 제공합니다.

#### 예제

```java

@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
```

```java
class Foo {
    public static List<T> filter(List<T> list, Predicate<T> p) {
        List<T> result = new ArrayList<>();
        for (T t : inventory) {
            if (p.test(t)) {
                result.add(t);
            }
        }
        return result;
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        List<String> nonEmpty = filter(listOfStrings, (s) -> !s.isEmplty());
    }
}
```

### 3.4.2 Consumer

`java.util.function.Consumer<T>`는 제네릭 형식의 `T` 객체를 전달 받아 `void`를 반환하는 `accpet` 추상 메소드를 제공합니다.

#### 예제

```java

@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```

```java
public interface Iterable<T> {
    default void forEach(Consumer<? super T> action) {
        Objects.requireNonNull(action);
        for (T t : this) {
            action.accept(t);
        }
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        List<Integer> integers = List.of(1, 2, 3, 4, 5);
        integers.forEach(number -> System.out.println(number));
    }
}
```

### 3.4.3 Function

`java.util.function.Function<T, R>`는 제네릭 형식의 `T`를 객체를 전달 받아 `R` 객체를 반환하는 `apply` 추상 메소드를 제공합니다.

#### 예제

```java

@FuncationalInterface
public interface Function<T, R> {
    R apply(T t);
}
```

```java
class Foo {
    public <T, R> List<R> map(List<T> list, Function<T, R> f) {
        List<R> result = new ArrayList<>();
        for (T t : list) {
            result.add(f.apply(t));
        }
        return result;
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        List<Integer> integers = List.of(1, 2, 3, 4, 5);
        map(integers, (number -> number + 1)); // 2, 3, 4, 5, 6
    }
}
```

#### 기본형 특화

`제네릭 파라미터`는 `참조형`만 사용할 수 있습니다. 그렇기 때문에 `기본형 타입`을 사용하면 `참조형 타입`으로 `박싱` 하게 됩니다.

하지만, `박싱`은 `기본 타입`을 `참조 타입`으로 변한하면 `Heep` 영역에 저장됩니다. 따라서 `박싱`한 값은 메모리를 더 소모하며 `기본형`을 가져올 떄도 메모리를 탐색하는 과정이 필요하므로 비용이 많이
듭니다.

> `Java 8`에서는 기본형을 입출력 사용하는 상황에서 `오토박싱`을 피할 수 있도록 특화된 `함수형 인터페이스`를 제공합니다.

```java

@FunctionalInterface
public interface IntPredicate {
    boolean test(int value);
}
```

```java
class Foo {
    public static void main(String[] args) {
        IntPredicate intPredicate = (i -> i % 2 == 0);
        intPredicate.test(1000); // true
    }
}
```

위의 `IntPredicate`는 `기본형 타입`을 그대로 사용하기 때문에 `오토박싱`이 일어나지 않아 기존의 `Predicate<T>`에 비해 효율적입니다.

> 이름에서 알수 있겠지만, `IntPredicate`외에도 `DoublePredicate`, `LongPredicate` 등 기본 타입을 모두 정의해 두었습니다.
>
> 다른 `함수형 인터페이스 (Function, Consumer 등)`들도 모두 같은 `네이밍 규칙`을 가지고 있습니다. `(ex: IntFunction<T, R>)`

#### 에외, 람다, 함수형 인터페이스의 관계

`함수형 인터페이스`에서는 확인된 예외를 던지는 동작을 허용하지 않습니다.

예외를 던지는 `Lambda expression`을 만들려면 `함수형 인터페이스`에 직접 정의하거나, `try ~ catch` 블록으로 감싸야합니다.

```java

@FunctionalInterface
public interface BufferedReaderProcessor {
    String process(BufferedReader b) throws IOException;
}
```

위의 `함수형 인터페이스`는 `IOException`을 던지고 있습니다.

`java.util.function.Function<T, R>`에 위의 `함수형 인터페이스`를 사용하고 싶은 경우, `Function<T, R>`에 에외를 정의할 수 없으니
`try ~ catch` 블록으로 감싸서 처리 해야합니다.

```java
class Foo {
    public static void main(String[] args) {
        Function<BufferedReader, String> f = (b) -> {
            try {
                return b.readLine();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        };
    }
}
```

## 3.5 형식 검사, 형식 추론, 제약

`Lambda`로 `함수형 인터페이스`의 `인스턴스`를 만들 수 있다고 했습니다.
`Lambda expresstion` 자체에는 어떤 `함수형 인터페이스`를 구현하는지에 대한 정보가 없습니다.

`Lambda expresstion`을 제대로 이해하려면 `Lambda`의 실제 형식을 파악해야 합니다.

### 3.5.1 형식 검사

`Lambda`가 사용되는 `Context`를 이용해서 형식을 추론할 수 있습니다.

> 어떤 `Context`에서 기대되는 `Lambda expression`의 형식을 `대상 형식 (target type)`이라고 합니다.

```java
class Foo {
    public static void main(String[] args) {
        List<Apple> heavierThan150g = filter(inventory, (Apple apple) -> apple.getWeight() > 150);
    }
}
```

위 식에서 형식 검사 과정은 아래와 같습니다.

1. `filter` 메소드의 선언을 확인
2. `filter` 메소드는 두 번째 파라미터로 `Predicate<Apple>` 형식(대상 형식)을 기대
3. `Predicate<Apple>`은 `test`라는 한 개의 `추상 메소드`를 정의하는 `함수형 인터페이스`
4. `test` 메소드는 `Apple`를 받아 `boolean`을 반환하는 `함수 디스크립터`를 묘사
5. `filter`의 두 번째 파라미터로 전달 된 인수는 이와 같은 요구사항을 만족해야 함

### 3.5.2 같은 람다, 다른 함수형 인터페이스

`대상 형식(target type)`이라는 특징 떄문에 같은 `Lambda expression`이더라도 호환되는 `추상 메소드`를 가진 다른 `함수형 인터페이스`로 사용될 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Callable<Integer> c = () -> 42;
        PrivilegedAction<Integer> p = () -> 42;
    }
}
```

`Callable`과 `PrivilegedAction` 모두 인자를 받지 않고 `T` 객체를 반환하는 `함수형 인터페이스`입니다. 따라서 같은 `Lambda expression`이지만 두 개 모두 유효합니다.

#### 다이아몬드 연산자

이미 `Java 7`에서 추가된 `다이아몬드 연산자(<>)`로 `Context`에 따른 제네릭 형식을 추론할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        List<String> strings = new ArrayList<>();
        List<Integer> integers = new ArrayList<>();
    }
}
```

이때, `인스턴스 표현식`의 `형식 인수`는 `Context`에 의해 추론됩니다.

#### 특별한 void 호환 규칙

`Lambda`의 `body`에 일반 표현식이 있으면 `void`를 반환하는 `함수 디스크립터`와 호환이 됩니다. (파라미터 리스트도 동일해야 함)

```java
class Foo {
    public static void main(String[] args) {
        Predicate<String> p = s -> list.add(s);
        Consumer<String> c = s -> list.add(s);

    }
}
```

`Predicate`는 `boolean`을 반환받으므로 유효하고, `Consumer`은 `void`를 반환받기 때문에 호환이 되어 유효합니다.

#### 함수 디스크립터가 동일한 경우

```java

@FunctionalInterface
class Foo {
    public void execute(Runnable runnable) {
        runnable.run();
    }

    public void execute(Action action) {
        action.act();
    }
}
```

```java

@FuncationalInterface
public interface Action {
    void act();
}
```

위와 같이 정의되어 있을 떄, `execute(() -> {})`라는 `Lambda expression`이 있다면 두 메소드의 `함수 디스크립터`가 동일하므로 어떤 메소드를 가리키는지 명확하지 않습니다.

이런 경우, `execute((Action) () -> {})` 처럼 캐스트를 하여 사용하면 명확해집니다.

### 3.5.3 형식 추론

`자바 컴파일러`는 `Lambda expression`이 사용된 `Context`를 이용해서 관련된 `함수형 인터페이스`를 추론합니다.

`대상 형식(target type)`을 이용해서 `함수 디스크립터`를 알 수 있으므로 `Lambda`의 `시그니처`도 추론이 가능합니다.

즉, `파라미터`에 타입을 생략할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Comparator<Apple> c1 = (Apple a1, Apple a2) -> ...
        Comparator<Apple> c2 = (a1, a2) -> ...
    }
}
```

두 번째 로직 처럼 단순하게 작성이 가능합니다.

> 꼭 생략하는것이 좋은것은 아닙니다. 상황에 따라 명시적으로 형식을 포함하는게 가독성에 더 좋을수도 있으므로,
> 작성하는 개발자가 결정하면 됩니다.
