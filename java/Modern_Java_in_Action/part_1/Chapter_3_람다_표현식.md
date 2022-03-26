# Chapter 3. 람다 표현식

- [3.1 람다란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#31-람다란-무엇인가)

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

```java
(parameters) -> expression  // `바디`가 한줄 이면 `return` 키워드를 생략할 수 있습니다.
```

또는 아래 처럼 `{}`안에 작성할 수 있습니다.

```java
(parameters) -> { statements; } // 이 경우에는 return 을 명시적으로 적어주어야 합니다.
```

