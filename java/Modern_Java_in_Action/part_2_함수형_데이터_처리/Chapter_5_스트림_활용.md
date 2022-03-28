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

