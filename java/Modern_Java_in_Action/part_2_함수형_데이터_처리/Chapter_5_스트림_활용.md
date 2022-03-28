# Chapter 5. 스트림 활용

- [5.1 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#51-필터링)
    - [5.1.1 프레이케이트로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#511-프레이케이트로-필터링)
    - [5.1.2 고유 요소 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#512-고유-요소-필터링)
- [5.2 스트림 슬라이싱](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#52-스트림-슬라이싱)
    - [5.2.1 프레디케이트를 이용한 슬라이싱](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#521-프레디케이트를-이용한-슬라이싱)
    - [5.2.2 스트림 축소](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#522-스트림-축소)
    - [5.2.3 요소 건너뛰기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#523-요소-건너뛰기)

`Stream`을 이용하면 필요 조건만 인수로 넘겨주면 데이터를 어떻게 처리할지는 `Stream API`가 관리하므로 편리하게 데이터 관련 작업을 할 수 있습니다.

또한, `Stream` 내부적으로 다양한 최적화가 일어날 수 있으며, `내부 반복` 외에도 `병렬`로 실행할지 여부도 결정할 수 있습니다.

> 순차적인 반복을 `Single Thread`로 구현하는 `외부 반복`으로는 할 수 없습니다.

`Java 8`과 `Java 9`에 추가된 다양한 연산에 대해 하나씩 알아보겠습니다.

## 5.1 필터링

`Predicate` 필터링 방법과 고유 요소만 필터링 하는 방법에 대해 알아보겠습니다.

### 5.1.1 프레이케이트로 필터링

`Stream`의 `filter` 메소드는 `Predicate`를 인수로 받아 `true`인 요소만 포함하는 `Stream`을 반환합니다.

```java
class Foo {
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
class Foo {
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
class Foo {
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
class Foo {
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
class Foo {
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
class Foo {
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
class Foo {
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
class Foo {
    public static void main(String[] args) {
        List<Dish> dishesSkip2 = menu.stream()
                .filter(d -> d.getCalories() > 300)
                .skip(2)
                .collect(toList());
    }
}
```

`filter`를 통해 추출 된 요소 중 `2개`를 건너 뛰고 나온 결과를 반환합니다.

