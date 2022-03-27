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
    - [3.5.4 지역 변수 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#354-지역-변수-사용)
- [3.6 메서드 참조](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#36-메서드-참조)
    - [3.6.1 요약](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#361-요약)
    - [3.6.2 생성자 참조](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#362-생성자-참조)
- [3.7 람다, 메서드 참조 활용하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#37-람다-메서드-참조-활용하기)
    - [3.7.1 1단계 : 코드 전달](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#371-1단계--코드-전달)
    - [3.7.2 2단계 : 익명 클래스 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#372-2단계--익명-클래스-사용)
    - [3.7.3 3단계 : 람다 표현식 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#373-3단계--람다-표현식-사용)
    - [3.7.4 4단계 : 메서드 참조 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#374-4단계--메서드-참조-사용)

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

### 3.5.4 지역 변수 사용

`Lambda expression`에서도 `익명 클래스` 처럼 `자유 변수 (파라미터로 넘겨진 변수가 아닌 외부에 정의 된 변수)`를 사용할 수 있습니다.

> 이와 같은 동작을 `람다 캡처링` 이라고 합니다.

```java
class Foo {
    public static void main(String[] args) {
        int portNumber = 1;
        Runnable r = () -> System.out.println(portNumber);
    }
}
```

#### 지역 변수의 제약

`지역 변수`를 사용함에 있어, 약간의 제약이 존재합니다.

`지역 변수`를 사용하려면 해당 변수는 `final`로 선언되어 있어야 하거나, 그와 동일한 의미로 사용되어야합니다. 즉, 변경되면 안됩니다.

그 이유는, `인스턴스 변수`는 `Heep` 영역에 저장되는 반면 `지역 변수`는 `Stack` 영역에 저장됩니다.  
만약 `Lambda`가 `지역 변수`에 바로 접근이 가능하다면 `Lambda`가 `Thread`에서 실행 될 경우 변수를 할당한 `Thread`가 사라져서 변수 할당이 해제 되었음에도 `Lambda`를
실행하는 `Thread`에서는 해당 변수에 접근하려고 할 수 있기 때문입니다.

따라서, `Java`에서는 해당 변수에 바로 접근을 허용하지 않고, 복사본을 제공합니다. 그렇기 때문에 `지역 변수`는 변경되면 안되므로 `final`로 선언하거나 그와 동일하게 사용되어야 하는 것 입니다.

이런 제약으로 인해 외부 변수를 변경시키는 일반적인 `명령형 프로그래밍 패턴`에 제동을 걸 수 있습니다.

> 인스턴스 변수는 `Thread`가 공유하는 `Heep` 영역에 존재하기 때문에 상관이 없습니다.

#### 클로저

`클로저`란 `함수`의 비지역 변수를 자유롭게 참조할 수 있는 `함수`의 인스턴스를 가리킵니다.

`클로저`는 `클로저` 외부에 정의된 변수의 값에 접근하고, 값을 바꿀 수도 있습니다.

`Java 8`의 `Lambda`와 `익명 클래스`는 `클로저`와 비슷한 동작을 수행합니다. 다만, `Lambda`와 `익명 클래스`는 외부의 값을 변경할 수 없다는데서 `클로저`와 차이가 있습니다.

덕분에 `Lambda`는 `변수`가 아닌 `값`에 국한되어 동작을 수행한다는 사실이 명확해집니다.

> 가변 지역 변수를 새로운 `Thread`에서 캡처할 수 있다면 안전하지 않은 동작을 수행할 가능성이 생깁니다.

## 3.6 메서드 참조

`메소드 참조`를 이용하면 기존의 메소드 정의를 재활용하여 `Lambda`처럼 전달할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort((a1, a2) -> a1.getWeight().compareTo(a2.getWeight()));
    }
}
```

위의 코드를 `메소드 참조`를 이용하면 아래처럼 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort(Comparator.comparing(Apple::getWeight));
    }
}
```

### 3.6.1 요약

`메소드 참조`는 `Lamnda`의 축약형이라고 생각할 수 있습니다.

예를 들어 Lambda`에서 해당 메소드를 실행해야 한다면, 해당 메소드를 어떻게 실행시키는지 설명을 참조하는 것보다 메소드명을 직접 참조 시키는것이 편리합니다.

`메소드 참조`를 이용하면 기존의 메소드로 `Lambda`를 만들 수 있습니다. 이때, 명시적으로 메소드 명을 참조함으로써 `가독성`을 높일 수 있습니다.

> `메소드 참조`는 `클래스명::메소드명` 형식으로 사용할 수 있습니다.
>
> `메소드 참조`는 새로운 기능이 아니라 하나의 메소드를 참조하는 `Lambda`르 편리하게 표현할 수 있는 문법입니다.

#### 메소드 참조를 만드는 방법

`메소드 참조`를 만드는 방법은 3가지가 있습니다.

- `정적 메소드 참조`
    - ex) `Integer`의 `parseInt` 메소드는 `Integer::parseInt`로 표현할 수 있습니다.
- `다양한 형식의 인스턴스 메소드 참조`
    - ex) `String`의 `length` 메소드는 `String::length`로 표현할 수 있습니다.
- `기존 객체의 인스턴스 메소드 참조`
    - ex) `Transaction`객체를 할당 받은 `expensiveTransaction` 지역 변수가 있고, `Transaction`객체는 `getValue` 메소드를 가지고
      있다면 `expensiveTransaction::getValue`로 표현할 수 있습니다.

3번 째의 경우 비공개 헬퍼 메소드를 정의한 상황에서 유용하게 사용될 수 있습니다.

```java
class Foo {
    private boolean isValidName(String str) {
        return Character.isUpperCase((String.charAt(0)));
    }
}
```

해당 메소드를 아래처럼 `Predicate<String>`을 필요로 하는 상황에 적절하게 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        filter(words, this::isValidName);
    }
}
```

`컴파일러`는 `Lambda expression`을 검사하던 방식과 비슷한 과정으로 `메소드 참조`가 주어진 `함수형 인터페이스`와 호환이 가능한지 확인합니다.

> 즉, `메소드 참조`는 `Context`형식과 일치해야 합니다.

### 3.6.2 생성자 참조

`ClassName::new`처럼 기존 `생성자`의 참조를 만들 수 있습니다. 이것은 `정적 메소드 참조`를 만드는 방법과 비슷합니다.

- 예를 들어 `Supplier`의 `() -> Apple` 시그니처를 갖는 `생성자`가 있다고 가정하면 아래 처럼 만들 수 있습니다. 아래 두 코드는 동일합니다.

```java
class Foo {
    public static void main(String[] args) {
        Supplier<Aple> c1 = Apple::new;
        Apple a1 = c1.get();
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        Supplier<Apple> c1 = () -> new Apple();
        Apple a1 = c1.get();
    }
}
```

- 인수가 하나인 `Apple(Integer weight)`라는 시그니처를 가진 `생성자`는 `Function<T, R>`의 형식과 동일하므로 아래처럼 작성할 수 있습니다. 아래 두 코드는 동일합니다.

```java
class Foo {
    public static void main(String[] args) {
        Function<Integer, Apple> c2 = Apple::new;
        Apple a2 = c2.apply(100);
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        Function<Integer, Apple> c2 = (weight) -> new Apple(weight);
        Apple a2 = c2.apply(100);
    }
}
```

- 인수를 두 개 받는 시그니차를 가진 `생성자`의 경우 `BiFunction<T, U, R>`의 형식과 동일하므로 아래 처럼 작성할 수 있습니다. 아래 두 코드는 동일합니다.

```java
class Foo {
    public static void main(String[] args) {
        BiFunction<Color, Integer, Apple> c3 = Apple::new;
        Apple a3 = c3.apple(GREEN, 100);
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        BiFunction<Color, Integer, Apple> c3 = (color, weight) -> new Apple(color, weight);
        Apple a3 = c3.apple(GREEN, 100);
    }
}
```

위에서 볼 수 있듯, `메소드 참조`를 이용하면 훨씬 간결하게 코드를 작성할 수 있습니다.

#### 인수가 3개 이상일 경우

위에서는 인수가 1개인 경우와 2개인 경우에 대해서 다뤘습니다. 하지만 인수를 3개 이상 받는 `생성자`의 경우는 정의 된 `함수형 인터페이스`가 없기 때문에 사용할 수가 없습니다.

그렇기 때문에 `시그니처`가 일치하는 `함수형 인터페이스`를 직접 만들어 사용해야 합니다.

```java
class TriFunction<T, U, V, R> {
    R apply(T t, U u, V v);
}
```

```java
class Foo {
    public static void main(String[] args) {
        TriFunction<Integer, Integer, Integer, Color> colorFactory = Color::new;
    }
}
```

## 3.7 람다, 메서드 참조 활용하기

처음에 다룬 사과 리스트를 `동작 파라미터화`, `익명 클래스`, `Lambda expression`, `메소드 참조`를 모두 사용하여, 더 간결하고 세련되게 만들어 보겠습니다.

- 최종 코드

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort(Comparator.comparing(Apple::getWeight));
    }
}
```

### 3.7.1 1단계 : 코드 전달

`Java 8`의 `List`는 `sort` 메소드를 제공합니다. 우리는 `sort` 메소드에 `정렬 전략`만 전달하면 됩니다.

`sort` 메소드의 `시그니처`는 아래와 같습니다.

```java
public interface List<E> extends Collection<E> {
    default void sort(Comparator<? super E> c) {
        ...
    }
}
```

`Comparator` 객체를 인수로 받아 두 사과를 비교합니다.

객체 안에 동작을 포함시키는 방식으로 다양한 `전략`을 전달할 수 있습니다.

즉, `sort`에 전달된 `정렬 전략`에 따라 `sort`의 동작이 달라질 것입니다.

- 아래처럼 작성할 수 있습니다.

```java
public class AppleComparator implements Comparator<Apple> {
    @Override
    public int compare(Apple a1, Apple a2) {
        return a1.getWeight().compareTo(a2.getWeight());
    }
}
```

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort(new AppleComparator());
    }
}
```

### 3.7.2 2단계 : 익명 클래스 사용

한 번만 사용된다면, `익명 클래스`를 이용하는 것이 더 좋습니다.

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort(new Comparator<Apple>() {
            @Override
            public int compare(Apple a1, Apple a2) {
                return a1.getWeight().compareTo(a2.getWeight());
            }
        });
    }
}
```

### 3.7.3 3단계 : 람다 표현식 사용

앞서 `익명 클래스`보다는 `Lambda expression`을 사용하는 것이 훨씬 더 간결하다는 것을 공부했습니다.

`함수형 인터페이스`를 기대하는 곳에는 어디든 `Lambda expression`을 사용할 수 있습니다.

`Comparator<T>`의 `함수 디스크립터`는 `(T, T) -> int` 이기 때문에 아래처럼 `Lambda`를 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort((a1, a2) -> a1.getWeight().compareTo(a2.getWeight()));
    }
}
```

`Comparator<T>`에는 `Comparable` 키를 추출하여 `Comparator`객체로 만드는 `Function`함수를 인수로 받는 정적 메소드 `comparing`를 포함하고 있습니다.

해당 메소드를 활용하면 위의 코드를 아래처럼 더 `가독성` 좋게 변경할 수 있습니다.

```java

class Foo {
    public static void main(String[] args) {
        inventory.sort(comparing(a -> a.getWeight()));
    }
}
```

> `static import`를 사용하여 `Comparator`도 생략하면 더 가독성이 좋습니다.

### 3.7.4 4단계 : 메서드 참조 사용

`메소드 참조`를 이용하면 `Lambda expression`의 인수를 더 깔끔하게 전달할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        inventory.sort(comparing(Apple::getWeight));
    }
}
```

이렇게 앞서 배운 모든 내용을 동원하여 최적의 코드를 완성했습니다.

> 이것은 단순히 코드만 짧아진 것이 아니라, 코드 자체로 '`Apple`을 `weight`별로 비교해서 `inventory`를 `sort`하라' 라는 코드의 의미도 명확해졌습니다.