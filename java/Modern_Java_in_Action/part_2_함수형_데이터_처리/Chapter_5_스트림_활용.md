# Chapter 5. 스트림 활용

- [5.1 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#51-필터링)
    - [5.1.1 프레이케이트로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#511-프레이케이트로-필터링)
    - [5.1.2 고유 요소 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#512-고유-요소-필터링)
- [5.2 스트림 슬라이싱](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#52-스트림-슬라이싱)
    - [5.2.1 프레디케이트를 이용한 슬라이싱](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#521-프레디케이트를-이용한-슬라이싱)
    - [5.2.2 스트림 축소](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#522-스트림-축소)
    - [5.2.3 요소 건너뛰기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#523-요소-건너뛰기)
- [5.3 매핑](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#53-매핑)
    - [5.3.1 스트림의 각 요소에 함수 적용하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#531-스트림의-각-요소에-함수-적용하기)
    - [5.3.2 스트림 평면화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#532-스트림-평면화)
- [5.4 검색과 매칭](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#54-검색과-매칭)
    - [5.4.1 프레디케이트가 적어도 한 요소와 일치하는지 확인](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#541-프레디케이트가-적어도-한-요소와-일치하는지-확인)
    - [5.4.2 프레디케이트가 모든 요소와 일치하는지 검사](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#542-프레디케이트가-모든-요소와-일치하는지-검사)
    - [5.4.3 요소 검색](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#543-요소-검색)
    - [5.4.4 첫 번째 요소 찾기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#544-첫-번째-요소-찾기)
- [5.5 리듀싱](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#55-리듀싱)
    - [5.5.1 요소의 합](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#551-요소의-합)
    - [5.5.2 최댓값과 최솟값](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#552-최댓값과-최솟값)
- [5.6 실전 연습](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#56-실전-연습)
    - [5.6.1 거래자와 트랜잭션](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#561-거래자와-트랜잭션)
- [5.7 숫자형 스트림](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#57-숫자형-스트림)
    - [5.7.1 기본형 특화 스트림](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#571-기본형-특화-스트림)

`Stream`을 이용하면 필요 조건만 인수로 넘겨주면 데이터를 어떻게 처리할지는 `Stream API`가 관리하므로 편리하게 데이터 관련 작업을 할 수 있습니다.

또한, `Stream` 내부적으로 다양한 최적화가 일어날 수 있으며, `내부 반복` 외에도 `병렬`로 실행할지 여부도 결정할 수 있습니다.

> 순차적인 반복을 `Single Thread`로 구현하는 `외부 반복`으로는 할 수 없습니다.

`Java 8`과 `Java 9`에 추가된 다양한 연산에 대해 하나씩 알아보겠습니다.

## 5.1 필터링

`Predicate` 필터링 방법과 고유 요소만 필터링 하는 방법에 대해 알아보겠습니다.

### 5.1.1 프레이케이트로 필터링

`Stream`의 `filter` 메소드는 `Predicate`를 인수로 받아 `true`인 요소만 포함하는 `Stream`을 반환합니다.

```java
class Filtering {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 2, 3, 4, 5);
        numbers.stream()
                .filter(n -> n > 2)
                .forEach(System.out::println);
        // 3, 4, 5

    }
}
```

`2`보다 큰 값들만 추출하는 방법입니다.

### 5.1.2 고유 요소 필터링

`Stream`은 고유 요소를 반환하는 `distinct`를 반환하는 메소드를 지원합니다.

`equals`와 `hasCode`를 기반으로 중복된 객체를 제거합니다.

```java
class Filtering {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 3, 2, 4, 2, 4, 6);
        numbers.stream()
                .filter(i -> i % 2 == 0)
                .distinct()
                .forEach(System.out::println);
        // 2, 4, 6
    }
}
```

짝수만 추출하여 중복 된 값은 제거하는 방법입니다.

## 5.2 스트림 슬라이싱

`Predicate`를 이용하는 방법, 처음 몇 개의 요소를 무시하는 방법, 특정 크기로 `Stream`을 줄이는 방법 등 다양한 방법을 이용해 효율적으로 `Stream`의 요소를 선택하거나 스킵할 수 있습니다.

### 5.2.1 프레디케이트를 이용한 슬라이싱

`Java 9`는 `takeWhile`, `dropWhile` 두 가지 메소드를 지원해, 요소를 통해 효과적으로 선택할 수 있습니다.

#### takeWhile 활용

```java
class Filtering {
    public static void main(String[] args) {
        List<Dish> specialMenu = Arrays.asList(
                new Dish("season fruit", true, 120, Dish.Type.OTHER),
                new Dish("prawns", false, 300, Dish.Type.FISH),
                new Dish("rice", true, 350, Dish.Type.OTHER),
                new Dish("chicken", false, 400, Dish.Type.MEAT),
                new Dish("french fries", true, 530, Dish.Type.OTHER));
    }
}
```

위의 요소를 `320 칼로리 이하`인 요소만 추출하기 위해서는 앞서 배운 `filter` 메소드를 이용할 것입니다.

하지만, `filter` 메소드는 모든 요소를 반복하기 때문에 요소가 많으면 많을수록 느려질수 있습니다.

위의 요소들은 이미 칼로리 별로 `정렬`이 되어 있는 상태이기 때문에, `320 칼로리`보다 큰 요소가 나오면 정지하는 것이 효과적입니다.

`taskWhile`을 이용하여 해당 작업을 할 수 있습니다.

```java
class Filtering {
    public static void main(String[] args) {
        List<Dish> slicedMenu1 = specialMenu.stream()
                .takeWhile(dish -> dish.getCalories() < 320)
                .collect(toList());
    }
}
```

#### dripWhile 활용

`dripWhile`은 `taskWhile`과 정 반대의 작업을 수행합니다.

`dripWhile`은 처음으로 `거짓`이 되는 지점까지 발견된 요소를 버리고 남은 요소를 반환합니다.

`dripWhile`은 `무한 스트림`에서도 동작합니다.

```java
class Filtering {
    public static final List<Dish> menu = Arrays.asList(
            new Dish("pork", false, 800, Dish.Type.MEAT),
            new Dish("beef", false, 700, Dish.Type.MEAT),
            new Dish("chicken", false, 400, Dish.Type.MEAT),
            new Dish("french fries", true, 530, Dish.Type.OTHER),
            new Dish("rice", true, 350, Dish.Type.OTHER),
            new Dish("season fruit", true, 120, Dish.Type.OTHER),
            new Dish("pizza", true, 550, Dish.Type.OTHER),
            new Dish("prawns", false, 400, Dish.Type.FISH),
            new Dish("salmon", false, 450, Dish.Type.FISH)
    );
}
```

```java
class Filtering {
    public static void main(String[] args) {
        List<Dish> slicedMenu2 = specialMenu.stream()
                .dropWhile(dish -> dish.getCalories() < 320)
                .collect(toList());
    }
}
```

### 5.2.2 스트림 축소

`limit` 메소드를 통해 특정 개수가 만족되면 `Stream`을 반환하도록 수 있습니다.

```java
class Filtering {
    public static void main(String[] args) {
        List<Dish> dishesLimit3 = menu.stream()
                .filter(d -> d.getCalories() > 300)
                .limit(3)
                .collect(toList());
    }
}
```

`300 칼로리`가 넘는 요소 중 3개만 추출하는 방법입니다. 이때, 전체를 순회하지 않고 `3개`개의 요소만 만족하면 즉시 `Stream`을 반환합니다.

### 5.2.3 요소 건너뛰기

`skip` 메소드는 처음 `n개` 요소를 제외한 `Stream`을 반환합니다.

```java
class Filtering {
    public static void main(String[] args) {
        List<Dish> dishesSkip2 = menu.stream()
                .filter(d -> d.getCalories() > 300)
                .skip(2)
                .collect(toList());
    }
}
```

`filter`를 통해 추출 된 요소 중 `2개`를 건너 뛰고 나온 결과를 반환합니다.

## 5.3 매핑

`SQL`의 `Table`에서 특정 열만 선택하는 것 처럼, 특정 객체의 특정 값만 선택하는 작업은 데이터 처리 과정에서 자주 수행되는 일입니다.

`Stream API`는 `map`과 `flatMap` 메소드를 통해 특정 열만 선택할 수 있도록 지원합니다.

### 5.3.1 스트림의 각 요소에 함수 적용하기

`map`메소드는 `함수`를 `인수`로 받아 `결과`로 나온 값들로 `새로운 Stream`을 만듭니다.

> 기존의 값을 `고친다`라는 개념이 아니라 `새로운 버전`을 만드는 것입니다.

```java
class Mapping {
    public static void main(String[] args) {
        List<String> dishNames = menu.stream()
                .map(Dish::getName)
                .collect(toList());
    }
}
```

위는 `요리 명`만 추출하는 것입니다.

### 5.3.2 스트림 평면화

`["Hello", "World]`라는 배열이 있을 떄, `고유 문자`만 추출하기 위해선 `split`으로 문자열을 자르고, `distinct`를 사용하여 중복을 제거하면 될거 같지만,
`split`을 통해 나온 결과는 `String[]` 형태이기 때문에 원하는 결과가 나오지 않습니다.

이렇게 `List`형식으로 이루어진 값들을 평평하게 펴서 처리할 수 있는 `flatMap` 메소드가 있습니다.

#### map과 Arrays.stream 활용

우선, `Array Stream`이 아니라 `String Stream`이 필요하므로 `T[]`를 입력받아 `Stream`을 생성하는 `Arrays.stream`을 이용하여 풀어보면 아래와 같습니다.

```java
class Mapping {
    public static void main(String[] args) {
        workd.stream()
                .map(w -> w.split("")) // 개별 문자 배열로 변환
                .map(Arrays::stream) // 각 배열을 별도의 스트림을 생성
                .distince()
                .collect(toList());

        // List<Stream<String>>>
    }
}
```

될 것 같았지만, 각 배열을 `Stream` 생성했기 때문에, `List<Stream>` 형태가 되어 여전히 해결되지 않았습니다.

#### flatMap 사용

`flatMap`은 각 배열을 `Stream`이 아닌 `Stream Content`로 매핑이 됩니다.

즉, `map`과는 달리 하나의 평면화 된 `Stream`을 반환합니다.

```java
class Mapping {
    public static void main(String[] args) {
        workd.stream()
                .map(w -> w.split(""))
                .flatMap(Arrays::stream)
                .distinct()
                .collect(toList());
    }
}
```

## 5.4 검색과 매칭

`allMatch`, `anyMatch`, `noneMatch`, `findFirst`, `findAny` 등 다양한 유틸리티 메소드를 이용하여 특정 속성이 집합에 있는지 여부를 검색할 수 있습니다.

### 5.4.1 프레디케이트가 적어도 한 요소와 일치하는지 확인

`anyMatch`는 `Predicate`를 인수로 받아 요소 중 하나라도 일치하면 `true`를 반환하는 메소드 입니다.

```java
class Finding {
    public static void main(String[] args) {
        if (menu.stream().anyMatch(Dish::isVegetarian)) {
            System.out.println("채식 요리 존재");
        }
    }
}
```

위의 코드는 `메뉴`에 `채식 요리`가 **하나라도 있는지 확인**하는 로직입니다.

### 5.4.2 프레디케이트가 모든 요소와 일치하는지 검사

`allMatch`는 `Predicate`를 인수로 받아 모든 요소가 모두 일치해야 `true`를 반환하는 메소드 입니다.

```java
class Finding {
    public static void main(String[] args) {
        menu.stream()
                .allMatch(dish -> dish.getCalories() < 1000);
    }
}
```

위의 코드는 `메뉴`의 `요리`가 **모두 1000 칼로리가 넘는지 확인**하는 로직입니다.

#### NoneMatch

`noneMatch`는 `allMatch`랑 반대의 연산을 수행합니다.

즉, 모두 일치하지 않아야 `true`를 반환합니다.

```java
class Finding {
    public static void main(String[] args) {
        menu.stream()
                .noneMatch(dish -> dish.getCalories() >= 1000);
    }
}
```

위의 코드와 `allMatch` 코드는 동일한 결과를 반환합니다.

> 위의 세 메소드는 `스트림 쇼트서킷 기법 (&&, || 같은)`을 사용하기 때문에, 조건이 부합하지 않으면 즉시 반환하도록 최적화되어 있습니다.

### 5.4.3 요소 검색

`findAny`는 현재 `Stream`에서 임의의 요소를 반환합니다.

```java
class Finding {
    public static void main(String[] args) {
        Optional<Dish> dish = menu.stream()
                .filter(Dish::isVegetarian)
                .findAny();
    }
}
```

위의 코드는 `채식 요리` 중 **하나를 반환**하는 로직입니다.

#### Optional 이란?

`Optional<T>` 클래스는 값의 존재나 부재 여부를 표현하는 `컨테이너 클래스` 입니다.

만약 위의 코드에서 `채식 요리`가 하나도 없으면 `null`을 반환하게 됩니다.
`null`은 `NullPointerException`을 유발할 수 있으니 가능한 피해야 합니다.

`Optional`을 사용하면 값의 존재 여부에 따라 다양한 동작을 수행할 수 있습니다.

- `boolen isPresent()`: 값이 존재하면 `true`를 반환합니다.
- `ifPresent(Consumer<T> block)`: `함수`를 `인자`로 받아 값이 존재하면 `함수`를 실행합니다.
- `T get()`: 값이 존재하면 값을 반환하고, 존재하지 않으면 `NoSuchElementException` 예외가 발생합니다.
- `T orElse(T other)`: 값이 있으면 반환하고, 값이 없으면 기본 값을 반환합니다.

```java
class Finding {
    public static void main(String[] args) {
        menu.stream()
                .filter(Dish::isVegetarian)
                .findAny()
                .ifPresent(dish -> System.out.println(dish.getName()));
    }
}
```

위 코드처럼 `null`을 검사할 필요없이 안전하게 작성할 수 있습니다.

### 5.4.4 첫 번째 요소 찾기

`findFirst`는 `Stream`에서 찾은 **첫 번째 요소를 반환**합니다.

```java
class Foo {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 2, 3, 4, 5);
        numbers.stream()
                .map(n -> n * n)
                .filter(n -> n % 3 == 0)
                .findFirst(); // 9
    }
}
```

> #### finFirst와 findAny는 언제 사용하나?
>
> `병렬 실행`에서는 `findFirst`로 첫 번쨰 요소를 찾기가 어렵습니다. 그렇기 때문에 반환 순서가 상관이 없다면 `findAny`를 사용합니다.

## 5.5 리듀싱

메뉴에서 모든 칼로리의 합계나 칼로리가 가장 높은 요리를 구할려면 `Integer` 같은 결과가 나올떄 까지 `Stream` 모든 요소를 반복적으로 처리 해야 합니다.

> 모든 `Stream` 요소를 처리해서 값으러 도출하는 이런 질의를 `리듀싱 연산`이라고 합니다.
>
> `함수형 프로그래밍` 언어 용어로는 `작은 조각`이 될 떄까지 반복해서 접는 것과 비슷하다는 의미로 `폴드`라고 부릅니다.

### 5.5.1 요소의 합

`for-each`를 사용하여 모든 요소의 합을 구하는 방법은 아래와 같습니다.

```java
class Foo {
    public static void main(String[] args) {
        int sum = 0;
        for (int n : numbers) {
            sum += n;
        }
    }
}
```

여기에서 `2가지 파라미터`를 사용했습니다.

- `sum`: 저장한 값을 보관 (초기값 0)
- `연산(+)`: `List`의 모든 요소를 조합

여기서 요구사항이 변경되어 `합(+)`이 아니라 `곱(*)`으로 바뀐다면, 앞서 배운 `동작 파라미터화`를 이용할 수 있습니다.

`Stream`에는 `reduce`라는 메소드를 제공합니다. `reduce`는 `2개의 인수`를 갖습니다.

- 초기값
- 두 요소를 조합해서 새로운 값을 만드는 `BinaryOperator<T>`

아래는 `reduce`를 이용한 버전입니다.

```java
class Foo {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 2, 3, 4, 5);
        int sum = numbers.stream()
                .reduce(0, (a, b) -> a + b);

        int sum = numbers.stream()
                .reduce(1, (a, b) -> a * b);
    }
}
```

`a`는 누적 값이며, `b`는 요소이기 떄문에 아래 처럼 동작하게 됩니다.

- `0 + 1`
- `1 + 2`
- `3 + 3` ...

`Integer`에는 두 숫자를 더하는 `sum` 메소드가 존재하기 떄문에 `메소드 참조`로 더 간결하게 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        numbers.stream().reduce(0, Integer::sum);
    }
}
```

#### 초기값 없음

`초기값`을 받지 않도록 `Override`된 `reduce`도 존재합니다.

이 `reduce`는 요소가 없으면 값이 존재하지 않을 수 있으므로 `Optional<T>`을 반환합니다.

### 5.5.2 최댓값과 최솟값

`최댓값`과 `최솟값`을 찾을 때도 `reduce`를 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Optional<Integer> number = numbers.stream().reduce((n1, n2) -> n1 > n2 ? n1 : n2); // 최댓값
    }
}
```

`Integer`에는 `최댓값`을 구하는 `max` 메소드를 지원하므로 `메소드 참조`를 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Optional<Integer> number = numbers.stream().reduce(Integer::min);
    }
}
```

`max`를 `min`으로 바꾸면 `최솟값`을 구할 수 있습니다.

> #### reduce 메서드의 장점과 병렬화
>
> `reduce`를 사용하지 않고 `for-each`를 사용해 구현을 할 수도 있지만,
> `for-each`를 사용하게 되면 `sum`이라는 변수를 공유해야 하므로 `병렬화`하기가 어렵습니다.
>
> 강제적으로 동기화를 시키더라도 결국 `병렬화`로 얻어야 할 이득이 `Thread`간의 소모적인 경쟁 떄문에 상쇄되어 버립니다.
>
> 즉, `가변 누적자 패턴 (mutable accumulator pattern)`은 `병렬화`와 거리가 너무 먼 기법입니다.
>
> `reduce`를 사용하면 `내부 반복`이 추상화 되면서 내부 구현에서 `병렬`로 처리가 가능합니다.
>
> `stream`을 `parallelStream`으로 변경하면 `병렬 처리`를 할 수 있습니다. 하지만 다음과 같은 대가를 지불해야합니다.
>
> - `reduce`로 넘겨준 `Lambda(인스턴스 변수 같은)`의 상태는 변경되면 안됩니다.
> - 어떤 순서로 실행되어도 결과가 같은 구조여야 합니다.

> #### 스트림 연산 : 상태 없음과 상태 있음
>
>`Stream`을 사용하여 원하는 모든 연산을 쉽게 구현할 수 있습니다. 하지만, 각각의 연산에 따라 내부적인 상태를 고려해야 합니다.
>
>`map`, `filter`등은 `input stream`에서 각 요소를 받아 0 또는 결과를 `output stream`으로 보내기 때문에 **내부상태를 갖지 않는 연산** 입니다.
>
>`reduce, sum, max` 같은 연산은 결과를 누적 하기 때문에 내부 상태가 필요합니다. `Stream`에서 처리하는 요소 수와 관계없이 내부 상태의 크기는 `한정`되어 있습니다.
>
>`sorted`, `distinct`같은 연산은 과거 이력을 알고 있어야 연산을 수행할 수 있습니다. 그렇기 때문에 **모든 요소가 버퍼에 추가**되어 있어야 합니다.
> 연산을 수행하기 위한 저장소 크기는 정해져 있지 않기 때문에 요소수가 무한이라면 문제가 생길 수 있습니다. 이러한 연산을 내부 상태를 갖는 연산이라고 합니다.

## 5.6 실전 연습

- 2011년에 일너난 모든 트랜잭션을 찾아 값을 오름차순으로 정렬
- 거래자가 근무하는 모든 도시를 중복 없이 나열
- 케임브리지에서 근무하는 모든 거래자를 찾아서 이름순으로 정렬
- 모든 거래자의 이름을 알파벳순으로 정렬해서 반환
- 밀라노에 거래자가 있는가?
- 케임브리지에 거주하는 거래자의 모든 트랜잭션값을 출력
- 전체 트랜잭션 중 최댓값은 얼마인가
- 전체 트랜잭션 중 최솟값을 얼마인가

### 5.6.1 거래자와 트랜잭션

```java
public class Trader {

    private String name;
    private String city;

    public Trader(String n, String c) {
        name = n;
        city = c;
    }

    public String getName() {
        return name;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String newCity) {
        city = newCity;
    }

    @Override
    public int hashCode() {
        int hash = 17;
        hash = hash * 31 + (name == null ? 0 : name.hashCode());
        hash = hash * 31 + (city == null ? 0 : city.hashCode());
        return hash;
    }

    @Override
    public boolean equals(Object other) {
        if (other == this) {
            return true;
        }
        if (!(other instanceof Trader)) {
            return false;
        }
        Trader o = (Trader) other;
        boolean eq = Objects.equals(name, o.getName());
        eq = eq && Objects.equals(city, o.getCity());
        return eq;
    }

    @Override
    public String toString() {
        return String.format("Trader:%s in %s", name, city);
    }

}

```

```java
public class Transaction {

    private Trader trader;
    private int year;
    private int value;

    public Transaction(Trader trader, int year, int value) {
        this.trader = trader;
        this.year = year;
        this.value = value;
    }

    public Trader getTrader() {
        return trader;
    }

    public int getYear() {
        return year;
    }

    public int getValue() {
        return value;
    }

    @Override
    public int hashCode() {
        int hash = 17;
        hash = hash * 31 + (trader == null ? 0 : trader.hashCode());
        hash = hash * 31 + year;
        hash = hash * 31 + value;
        return hash;
    }

    @Override
    public boolean equals(Object other) {
        if (other == this) {
            return true;
        }
        if (!(other instanceof Transaction)) {
            return false;
        }
        Transaction o = (Transaction) other;
        boolean eq = Objects.equals(trader, o.getTrader());
        eq = eq && year == o.getYear();
        eq = eq && value == o.getValue();
        return eq;
    }

    @SuppressWarnings("boxing")
    @Override
    public String toString() {
        return String.format("{%s, year: %d, value: %d}", trader, year, value);
    }

}
```

#### 스스로 풀어본 답

```java
public class TransactionTest {
    public static void main(String[] args) {

        Trader raoul = new Trader("Raoul", "Cambridge");
        Trader mario = new Trader("Mario", "Milan");
        Trader alan = new Trader("Alan", "Cambridge");
        Trader brian = new Trader("Brian", "Cambridge");

        List<Transaction> transactionList = List.of(
                new Transaction(brian, 2011, 300),
                new Transaction(raoul, 2012, 1000),
                new Transaction(raoul, 2011, 400),
                new Transaction(mario, 2012, 710),
                new Transaction(mario, 2012, 700),
                new Transaction(alan, 2012, 950));

        System.out.println("1. 2011년에 일어난 모든 트랜잭션을 찾아 값을 오름차순으로 정렬"); // 정답
        transactionList.stream()
                .filter(transaction -> transaction.getYear() == 2011)
                .sorted(Comparator.comparing(Transaction::getValue))
                .forEach(System.out::println);

        System.out.println("2. 거래자가 근무하는 모든 도시를 중복 없이 나열"); // 정답
        transactionList.stream()
                .map(transaction -> transaction.getTrader().getCity())
                .distinct()
                .forEach(System.out::println);

        System.out.println("3. 케임브리지에서 근무하는 모든 거래자를 찾아서 이름순으로 정렬"); // 틀림
        transactionList.stream()
                .map(Transaction::getTrader)
                .filter(trader -> trader.getCity().equals("Cambridge"))
                .distinct() // 중복없도록 확인 (이 부분 빼먹음)
                .sorted(Comparator.comparing(Trader::getName))
                .forEach(System.out::println);

        System.out.println("4. 모든 거래자의 이름을 알파벳순으로 정렬해서 반환"); // 완전 틀림
        transactionList.stream()
                .map(transaction -> transaction.getTrader().getName())
                .sorted(String::compareTo)
                .forEach(System.out::println);

        // 4. 정답
        String reduce = transactionList.stream()
                .map(transaction -> transaction.getTrader().getName())
                .distinct()
                .sorted()
                .reduce("", (s1, s2) -> s1 + s2);


        System.out.println("5. 밀라노에 거래자가 있는가?"); // 틀린건 아니지만 더 간결한 방법이 있음
        transactionList.stream()
                .filter(transaction -> transaction.getTrader().getCity().equals("Milan"))
                .findAny()
                .ifPresent(transaction -> System.out.println(true));

        // 5. 더 간결한 방법
        transactionList.stream()
                .anyMatch(transaction ->
                        transaction.getTrader().getCity().equals("Milan")
                );

        System.out.println("6. 케임브리지에 거주하는 거래자의 모든 트랜잭션값을 출력"); // 오해
        transactionList.stream()
                .filter(transaction -> transaction.getTrader().getCity().equals("Cambridge"))
                .map(Transaction::getValue) // 그 값이 이 값이 였구나
                .forEach(System.out::println);

        System.out.println("7. 전체 트랜잭션 중 최댓값은 얼마인가");
        transactionList.stream()
                .reduce((t1, t2) -> t1.getValue() > t2.getValue() ? t1 : t2)
                .ifPresent(transaction -> System.out.println(transaction.getValue()));

        System.out.println("8. 전체 트랜잭션 중 최솟값을 얼마인가");
        transactionList.stream()
                .reduce((t1, t2) -> t1.getValue() < t2.getValue() ? t1 : t2)
                .ifPresent(transaction -> System.out.println(transaction.getValue()));

        // 7, 8 더 깔끔한 방법
        transactionList.stream()
                .map(Transaction::getValue)
                .reduce(Integer::max)
                .ifPresent(System.out::println);
    }
}
```

## 5.7 숫자형 스트림

`reduce`로 합을 구하는 예제에는 `박싱 비용`이라는 함정이 숨어있습니다. 내부적으로 합계를 계산하기 전에 `Integer`를 `int`로 `언박싱`을 해야 합니다.

```java
class Foo {
    public static void main(String[] args) {
        menu.stream()
                .map(Dish::getCalories)
                .reduce(0, Integer::sum);
    }
}
```

아래 예제처럼 `sum`을 직접 호출 하는것이 `reduce`를 사용하는것 보다 직관적이고 더 좋습니다.

```java
class Foo {
    public static void main(String[] args) {
        menu.stream()
                .map(Dish::getCalories)
                .sum(); // 지원하지 않음
    }
}
```

하지만, `stream`은 해당 기능을 지원하지 않습니다. 해당 객체가 `숫자`인지 `일반 객체`인지 알 수 없고, `일반 객체`의 경우 `sum`을 사용할 수도 없기 때문입니다.

그래서 `Stream`은 `기본형 특화 Stream`을 제공합니다.

### 5.7.1 기본형 특화 스트림

`Java 8`에는 `박싱 비용`을 피할 수 있도록 `IntStream`, `DoubleStream`, `LongStream` 세 가지의 특화된 `Stream`을 제공합니다.

`min`, `max` 같은 자주 사용하는 숫자 관련 `reducing` 연산을 제공합니다.

> `특화 Stream`은 `박싱 비용`에만 관련 있으며, `Stream`에 대한 추가 기능은 제공하지 않습니다.

#### 숫자 스트림으로 매핑

`Stream`을 ` 특화 Stream`으로 변환할 떄는 `mapToInt`, `mapToDouble`, `mapToLong` 세가지 메소드를 가장 많이 사용합니다,.

```java
class Foo {
    public static void main(String[] args) {
        int calories = menu.stream()
                .mapToInt(Dish::getCalories)
                .sum();
    }
}
```

`mapToInt`를 사용했기 때문에 `IntStream`이 반환되어 `sum` 메소드로 간단하게 합계를 구할 수 있으며, `박싱 비용`도 아낄수 있습니다.

#### 객체 스트림으로 복원하기

`IntStream`에서 다시 `일반 Stream`으로 변경하기 위해선 `boxed` 메소드를 이용하면 됩니다.

```java
class Foo {
    public static void main(String[] args) {
        IntStream intStream = menu.stream.mapToInt(Dish::getCalories);
        Stream<Integer> stream = intStream.boxed();
    }
}
```

#### 기본값 : OptionalInt

합계의 경우 값이 기본겂이 `0`이여도 문제가 없습니다. 하지만, `최댓값`, `최솟값` 같은 경우 실제 값이 `0`인지, 아니면 요소가 존재하지 않는지에 따라 잘못된 결과를 낼 수 있습니다.

객체의 경우 `Optional<T>`로 감싸서 `null`로 부터 안전했지만, 기본 타입의 경우 `Optional<T>`를 사용할 수 없습니다. (사용하기 위해선 `박싱`이 필요)

`특화 스트림`은 `OptionalInt`, `OptionalDouble`, `OptionalLong`를 제공하여 `Optional<T>`와 동일하게 사용할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        IntStream intStream = menu.stream.mapToInt(Dish::getCalories);
        int max = intStream.max().orElse(1);
    }
}
```

### 5.7.2 숫자 범위

개발을 하다보면 `특정 범위`의 숫자를 생성해야 하는 경우가 많습니다.

`IntStream`은 `range`와 `rangeClosed` 두 메소드를 제공합니다. 두 메소드 모두 `시작값`과 `종료값` 인수를 가지며,
`ragne`는 `종료값`이 포함되지 않는 다는 차이가 있습니다. (`range <` `rangeClosed <=`)

```java
class Foo {
    public static void main(String[] args) {
        System.out.println(IntStream.rangeClosed(1, 100).filter(n -> n % 2 == 0).count()); // 50
    }
}
```

> 책에서는 `range`가 `시작값`과 `종료값`을 포함하지 않는다고 되어 있는데, 테스트 결과 `종료값`만 포함하지 않았습니다.

### 5.7.3 숫자 스트림 활용 : 피타고라스 수

`피타고라스 수`를 만들며 조금 더 `Stream`연산을 익혀보겠습니다.

#### 피타고라스 수

`피타고라스 수`는 `(a * a) + (b * b) = (c * c)`를 만족하는 `a`, `b`, `c` 세 정수입니다. 예를 들어 `(3 * 3) + (4 * 4) + (5 * 5)`는 `9 + 16 + 25`
이므로 식이 만족합니다.

#### 세 수 표현하기

`class`를 만드는 것 보다는 세 요소를 갖는 `int[]`을 만들어 `index`로 접근하여 사용하면 간단하게 사용할 수 있습니다.
`new int[]{3, 4, 5}` 처럼 사용할 수 있습니다.

#### 좋은 필터링 조합

`a`, `b` 두 수만 제공한다고 했을 때, `(a * a) + (b * b)`의 `제곱근`이 정수인지 확인하면 `피타고라스 수`에 부합하는지 알 수 있습니다.
`부동 소수점`의 경우 `n % 1`으로 거를 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        filter(b -> Math.sqrt((a * a) + (b * b)) % 1 == 0);
    }
}
```

위 코드에서 `a`라는 값이 주어지고  `b`는 `Stream`으로 제공된다고 가정할 때 `filter`로 `a`와 함께 `피타고라스 수`를 구성하는 모든 `b`를 `filtering`할 수 있습니다.

#### 집합 생성

`filter`를 통해 좋은 조합을 갖는 `a`, `b`를 선택했으니, `map`을 사용하여 각 요소를 `피타고라스 수`로 변환할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        stream.filter(b -> Math.sqrt((a * a) + (b * b)) % 1 == 0)
                .map(b -> new int[]{a, b, (int) Math.sqrt((a * a) + (b * b))});
    }
}
```

#### b값 생성

`Stream.rangeClosed`를 사용하여 주어진 범위의 수를 생성하여 `b` 값을 만들어 줍니다.

```java
class Foo {
    public static void main(String[] args) {
        IntStream.rangeClosed(1, 100)
                .filter(b -> Math.sqrt((a * a) + (b * b)) % 1 == 0)
                .boxed()
                .map(b -> new int[]{a, b, (int) Math.sqrt((a * a) + (b * b))});
    }
}
```

중간에 `boxed`로 `int` 타입을 `Integer`로 만들어 주었습니다. 해당 작업을 하지 않으면 `IntStream`의 `map`은 `int` 반환을 기대하므로 `int[]`을 반환할 수 없습니다.

```java
class Foo {
    public static void main(String[] args) {
        IntStream.rangeClosed(1, 100)
                .filter(b -> Math.sqrt((a * a) + (b * b)) % 1 == 0)
                .mapToObj(b -> new int[]{a, b, (int) Math.sqrt((a * a) + (b * b))});
    }
}
```

`mapToObj`를 사용하면 조금 더 간결하게 작성이 가능합니다.

#### a 값 생성

이제 `a`만 생성함면 `피타고라스 수`를 생성하는 `Stream`을 완성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Stream<int[]> pythagoreanTriples =
                IntStream.rangeClosed(1, 100)
                        .boxed()
                        .flatMap(a ->
                                IntStream.rangeClosed(a, 100)
                                        .filter(b -> Math.sqrt((a * a) + (b * b)) % 1 == 0)
                                        .mapToObj(b -> new int[]{a, b, (int) Math.sqrt((a * a) + (b * b))})
                        );
    }
}
```

조금 복잡해 보일 수 있지만, 하나하나 뜯어보면 어렵지 않습니다.

- 우선 `IntStream`의 `rangeClosed`를 통해 `1 ~ 100`의 `a`를 생성합니다.
- `flatMap`을 사용하여 위에서 작성 했던 `b` 생성 로직을 작성합니다.
- `b`생성 로직에서 `시작값`이 `a`로 변경되었습니다. 만약 `1 ~ 100`으로 했다면 `(3, 4, 5)`와 `(4, 3, 5)`처럼 중복 값이 발생할 수 있습니다.

> `flatMap`을 사용하지 않고 `map`을 사용하면 `Stream<Stream<int[]>>` 형태가 되어버립니다.

#### 코드 실행

`limit`를 이용해서 얼마나 많은 세 수를 포함하는 `Stream`을 만들지만 결정하면 됩니다.

```java
class Foo {
    public static void main(String[] args) {
        pythagoreanTriples.limit(5)
                .forEach(t -> System.out.println("%d, %d, %d".formatted(t[0], t[1], t[2])));
    }
}
```

#### 개선할 점?

현재는 `제곱근`을 두 번 계산합니다. 따라서 `(a * a) + (b * b) = (c * c)`를 만족하는 세 수를 만든 다음 `filtering`하는 것이 더 최적화됩니다.

```java
class Foo {
    public static void main(String[] args) {
        Stream<double[]> pythagoreanTriples2 = IntStream.rangeClosed(1, 100)
                .boxed()
                .flatMap(
                        a -> IntStream.rangeClosed(a, 100)
                                .mapToObj(b -> new double[]{a, b, Math.sqrt((a * a) + (b * b))})
                                .filter(t -> t[2] % 1 == 0)
                );
    }
}
```
