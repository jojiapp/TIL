# Chapter 6. 스트림으로 데이터 수집

- [6.1 컬렉터란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#61-컬렉터란-무엇인가)
    - [6.1.1 고급 리듀싱 기능을 수행하는 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#611-고급-리듀싱-기능을-수행하는-컬렉터)
    - [6.1.2 미리 정의된 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#612-미리-정의된-컬렉터)
- [6.2 리듀싱과 요약](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#62-리듀싱과-요약)
    - [6.2.1 스트림값에서 최댓값과 최솟값 검색](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#621-스트림값에서-최댓값과-최솟값-검색)
    - [6.2.2 요약 연산](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#622-요약-연산)
    - [6.2.3 문자열 연결](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#623-문자열-연결)
    - [6.2.4 범용 리듀싱 요약 연산](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#624-범용-리듀싱-요약-연산)
- [6.3 그룹화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#63-그룹화)
    - [6.3.1 그룹화된 요소 조작](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#631-그룹화된-요소-조작)
    - [6.3.2 다수준 그룹화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#632-다수준-그룹화)
    - [6.3.3 서브그룹으로 데이터 수집](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#633-서브그룹으로-데이터-수집)
- [6.4 분할](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#64-분할)
    - [6.4.1 분할의 장점](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#641-분할의-장점)
    - [6.4.2 숫자를 소수와 비소수로 분할하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#642-숫자를-소수와-비소수로-분할하기)
- [6.5 Collector 인터페이스](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#65-Collector-인터페이스)
    - [6.5.1 Collector 인터페이스의 메서드 살펴보기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#651-Collector-인터페이스의-메서드-살펴보기)
    - [6.5.2 응용하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#652-응용하기)

`Java 8`의 `Stream`은 **데이터 집합을 멋지게 처리하는 게으른 반복자**라고 설명할 수 있습니다.

`Stream`의 연산은 한 `Stream`을 다른 `Stream`으로 변환하는 중간 연산 (`map`, `filter` 등)과
`Stream`의 요소를 소비해서 최종 결과를 도출하는 최종 연산 (`count`, `findFirst`, `forEach,`, `reduce` 등)으로 구분할 수 있습니다

최종 연산은 `Stream Pipeline`을 최적화하면서 계산 과정을 짧게 생략하기도 합니다.

앞서 `collect`를 이용해서 `toList`만 사용해봤습니다.
`collect`역시 `reduce` 처럼 다양한 요소 누적 방식을 인수로 받아서 `Stream`의 최종 결과로 도출하는 `reducing 연산`을 수행할 수 있습니다.

다양한 요소 누적 방식은 `interface Collector`에 정의되어 있습니다.

통화별로 트랜잭션을 `그룹화` 하기 위해서 기존에는 아래와 같이 작성했습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Currency, List<Transaction>> transactionsByCurrencies = new HashMap<>();

        for (Transaction transaction : transactions) {
            Currency currency = transaction.getCurrency();
            List<Transaction> transactionsForCurrency =
                    transactionsByCurrencies.get(currency);

            if (transactionsForCurrency == null) {
                transactionsForCurrency = new ArrayList<>();
                transactionsByCurrencies.put(currency, transactionsForCurrency);
            }
            transactionsForCurrency.add(transaction);
        }
    }
}
```

간단한 작업임에도 코드도 너무 길고, 해당 로직이 어떤 로직인지 한 눈에 파악하기도 어렵습니다.

`Collector`를 이용하면 아래와 같이 구현할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Currency, List<Transaction>> transactionsByCurrencies =
                transactions.stream().collect(groupingBy(Transaction::getCurrency));
    }
}
```

놀라울 정도로 줄어든 코드와 한 눈에 봐도 `통화`를 기준으로 `그룹화`하라는 게 보입니다.

## 6.1 컬렉터란 무엇인가?

위의 예제를 통해 `명령형 프로그래밍`에 비해 `함수형 프로그래밍`이 얼마나 편리한지 명확하게 보여줍니다.

`함수형 프로그래밍`은 `무엇`을 원하는지 직접 명시할 수 있어, 어떤 방법으로 이를 얻을지는 신경 쓰지 않아도 됩니다.

`다수준`으로 `그룹화`를 수행할 때, `명령형 프로그래밍`과 `함수형 프로그래밍`의 차이는 더 두드러집니다.

`명령형`의 경우 다중 루프와 조건물을 추가해야 하기 때문에 `가독성`과 `유지보수성`이 크게 떨어지는 반면,
`함수형`에서는 필요한 `Collector`를 쉽게 추가할 수 있습니다.

### 6.1.1 고급 리듀싱 기능을 수행하는 컬렉터

훌륭하게 설계된 `함수형 API`의 또 다른 장점으로는 높은 수준이 `조합성`과 `재사용성`을 꼽을 수 있습니다.

`collect`에서는 `reducing 연산`을 이용해서 `Stream`의 각 요소를 방문하면서 `Collector`가 작업을 처리합니다.

> `collect`로 결과를 수집하는 과정을 간단하면서도 유연한 방식으로 정의할 수 있다는 점이 `Collector`의 최대 강점입니다.

보통 함수를 요소로 변환 할 때는 `Collector`를 적용하며, 최종 결과를 저장하는 자료구조에 값을 누적합니다.

```java
class Foo {
    private static Map<Dish.Type, List<Dish>> groupDishesByType() {
        return menu.stream().collect(Collectors.groupingBy(Dish::getType));
    }
}
```

예를 들어 `groupingBy`을 이용하면, `특정 필드`를 기준으로 `그룹화`를 하면, `key`값으로 `그룹화`에 사용한 `특정 필드`가, `value`에 해당 데이터가 들어간 `Map`을 반환합니다. 위의
경우 `Dish`의 `type`이 `key`값이 되고, `Dish`가 `value`가 됩니다.

위 처럼, `Collectors` `interface`의 메소드를 어떻게 구현하느냐에 따라 `Stream`에 어떤 `reducing 연산`을 숳ㅇ할 지 결정됩니다.

### 6.1.2 미리 정의된 컬렉터

`Collectors`에서 제공하는 메소드의 기능은 크게 세 가지로 구분할 수 있습니다.

- `Stream` 요소를 하나의 값으로 `reduce`하고 `요약`
    - `총합`을 찾는 등의 작업을 할 때 유용합니다.
- `그룹화`
    - `다수준`으로 `그룹화` 하거나, 각각의 결과를 `서브 그룹`에 추가로 `reducing 연산`을 적용할 수 있습니다.
- `분할`
    - `그룹화`의 특별한 연산으로, `Predicate`를 `그룹화 함수`로 사용합니다.

## 6.2 리듀싱과 요약

`Collector`로 `Stream`의 모든 항목을 하나의 결과로 함칠 수 있습니다.

트리를 구성하는 다수준 `Map`, 메뉴의 칼로리 합계를 가리키는 `단순한 정수` 등 다양한 형식으로 결과가 도출 될 수 있습니다.

예를 들어, 메뉴의 전체 개수를 알고 싶다면 아래와 같이 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        menu.stream().collect(Collectors.counting());
    }
}
```

아래처럼 불필요한 과정을 생략하여 더 간단하게 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        menu.stream().count();
    }
}
```

### 6.2.1 스트림값에서 최댓값과 최솟값 검색

`Collectors.maxBy`와 `Collectors.minBy`를 통해 `최댓값`과 `최솟값`을 구할 수 있습니다. 두 `Collector`는 `Comparator`를 인자로 받아 계산을 수행합니다.

예를 들어, 메뉴에서 칼로리가 가장 높은 요리를 찾는다고 하면 아래와 같이 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Optional<Dish> mostCalorieDish = menu
                .stream()
                .collect(maxBy(Comparator.comparingInt(Dish::getCalories)));

        // 더 간단하게 작성
        menu.stream().max(Comparator.comparingInt(Dish::getCalories));

    }
}
```

특이한 점은 `Optional`을 반환한다는 점입니다.

만약, 요소가 하나도 반환할 값이 없기 떄문에 `Optional`로 감싸져서 반환되는 것입니다.

> `Stream`에 있는 숫자 필드의 `합계`나 `평균` 등을 반환하는 연산에도 `reducing` 기능이 자주 사용됩니다.
>
> 이러한 연산을 `요약 (summariztion)` 연산이라 부릅니다.

### 6.2.2 요약 연산

`class Collectors`는 `summingInt`라는 특별한 요약 팩토리 메소드를 제공합니다.

```java
class Foo {
    public static void main(String[] args) {
        int totalCalories = menu.stream().collect(summingInt(Dish::getCalories));
    }
}
```

`summingInt`의 `인수`로 전달된 `함수`는 `객체`를 `int`로 `Mapping`한 `Collector`를 반환하고,
`collect` 메소드로 전달되면 `요약 작업`을 수행합니다.

`summingLong`와 `summingDobule`는 `long`, `double` 형식의 데이터로 요약한다는 점만 다르고 동작은 동일합니다.

`합계`외에도 `평균`을 구하기 위한 `averagingInt`도 있습니다. (물론 `long`, `double`도 제공)

또한 `개수`, `합계`, `평균`, `최솟값`, `최댓값`을 한 번에 연산해주는 `summarizingInt` 메소드를 제공합니다.

```java
class Foo {
    public static void main(String[] args) {
        IntSummaryStatistics menuStatistics = menu.stream().collect(summarizingInt(Dish::getCalories));
        System.out.println(menuStatistics);
        // IntSummaryStatistics{count=9, sum=4300, min=120, average=477.777778, max=800}
    }
}
```

물론, `long`과 `double`에 특화된 `summarizingLong`와 `summarizingDouble` 및 `LongSummaryStatistics`, `DoubleSummaryStatistics`도
있습니다.

### 6.2.3 문자열 연결

`Collector`의 `joining` 팩토리 메소드를 이용하면 ~~각 객체의`toString`을 호출~~ 하여 추출한 모든 문자열을 하나의 문자열로 연결해서 반환합니다.

`joining` 메소드는 내부적으로 `StringBuilder`를 이용해서 문자열을 하나로 만듭니다.

```java
class Foo {
    public static void main(String[] args) {
        String shortMenu = menu.stream().map(Dish::getName).collect(joining());
    }
}
```

위는 메뉴의 모든 요리 이름을 연결하여 한줄로 출력하는 로직입니다.

```java
class Foo {
    public static void main(String[] args) {
        String shortMenu1 = menu.stream().collect(joining()); // 불가능
        String shortMenu2 = menu.stream().map(Dish::toString).collect(joining()); // 가능
    }
}
```

> 테스트 결과 자동으로 `toString`을 호출 하지 않으므로 `joining`전에 `String`형식으로 변환 작업을 해주어야 합니다.

`구분자`를 넣고 싶다면 `joining(", ")`와 같은 형식으로 넣어줄 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        String shortMenu = menu.stream().map(Dish::toString).collect(joining(", "));
    }
}
```

두 번째 인수로 `prefix`, 세 번째 인수로 `suffix`를 받으므로 시작과 끝에 필요한 작업이 있다면 아래 처럼 작성할수도 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        String collect = menu.stream().map(Dish::toString).collect(joining(", ", "{", "}"));
    }
}
```

### 6.2.4 범용 리듀싱 요약 연산

지금까지 살펴본 모든 `Collector`는 `reducing` 팩토리 메소드로도 정의할 수 있습니다. 그럼에도 `특화된 Collector`를 사용하는 이유는 `프로그래밍적 편의성`과 `가독성` 때문입니다.

아래 처럼 작성하여 모든 요리의 칼로리의 합계를 구할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Integer totalCalories = menu.stream().collect(reducing(
                        0, Dish::getCalories, (i, j) -> i + j
                )
        );
    }
}
```

`reducing` 메소드는 세 개의 인수를 받습니다.

1. `reducing` 연산의 `시작값` 이거나 `Stream`의 인수가 없을 때 `반환값`
2. `변환 함수`
3. `BinaryOperator` 함수

아래 처럼 작성하여 칼로리가 가장 높은 요리를 추출할 수도 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Optional<Dish> mostCalorieDish = menu.stream().collect(reducing(
                        (d1, d2) -> d1.getCalories() > d2.getCalories() ? d1 : d2
                )
        );
    }
}
```

`한 개의 인수`를 갖는 `reducing` 메소드는 세 개의 인수를 갖는 `reducing` 메소드에서
`Stream`의 `첫 번째 요소`를 `시작 요소`로, `두 번째 요소`로 자신을 반환하는 `항등 함수`를 받습니다.

첫 번째 요소가 없으면 값이 존재 하지 않으므로 `Optional` 객체를 반환합니다.

> #### collect와 reduce
>
> `collect`와 `reduce` 메소드는 같은 기능을 구현할 수 있으므로 다른 점이 무엇인지 애매할 수 있습니다.
>
> `collect`대신 `reduce` 메소드로 `toList`를 구현 한다면 아래처럼 작성할수 있습니다.
>
> ```java
> class Foo {
>     public static void main(String[] args) {
>         List<Integer> reduce = Stream.of(1, 2, 3, 4, 5)
>                 .reduce(
>                         new ArrayList<>(),
>                         (List<Integer> l, Integer e) -> {
>                             l.add(e);
>                             return l;
>                         },
>                         (List<Integer> l1, List<Integer> l2) -> {
>                             l1.addAll(l2);
>                             return l1;
>                         }
>                 );
>     }
> }
> ```
>
> 위 코드는 `의미론적인 문제`와 `실용성 문제` 두 가지 발생합니다.
>
> `collect` 메소드는 도출하려는 결과를 누적하는 컨테이너를 바꾸도록 설계된 반면,
> `reduce`는 두 값을 하나로 도출하는 불변형 연산이라는 점에서 `의미론적 문제`가 일어납니다.
>
> 위의 에제는 누적자로 사용된 리스트를 변환시키므로 `reduce` 메소드를 잘못 활용한 예에 해당합니다.
>
> 또한, `Thread`가 동시에 같은 데이터 구조체를 고치면 리스트 자체가 망가져버리므로 `reducing 연산`을 `병렬`로 수행할 수 없다는 점도 문제입니다.
> 해당 문제를 해결하기 위해선 매번 새로운 리스트를 할당해야 하고, 따라서 객체를 할당하느라 성능이 저하될 것입니다.
>
> 그렇기 때문에 `가변 컨테이너` 관련 작업이면서 `병렬성`을 확보하려면 `collect`를 사용하는 것이 바람직합니다.

#### 컬렉션 프레임워크 유연성 : 같은 연산도 다양한 방식으로 수행할 수 있다.

위에서 작성했던 모든 요리의 칼로리 합계를 구하는 `reducing` 작업을 `Lambda`대신 `Integer`의 `sum` 메소드를 `메소드 참조`로 이용하면 코드를 더 단순화 시킬수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Integer totalCalories2 = menu.stream()
                .collect(
                        reducing(
                                0,
                                Dish::getCalories,
                                Integer::sum
                        )
                );

        // totalCalories2 보다 더 깔끔 (박싱 비용 발생 O)
        Optional<Integer> totalCalories3 = menu.stream()
                .map(Dish::getCalories)
                .reduce(Integer::sum);


        // totalCalories3 보다 성능 좋음 (박싱 비용 발생 X)
        int totalCalories4 = menu.stream()
                .mapToInt(Dish::getCalories)
                .sum();
    }
}
```

`counting`의 경우도 `reducing` 메소드를 이용하여 구현할 수 있습니다.

```java
class Foo {
    public static <T> Collector<T, ?, Long> counting() {
        return reducing(0L, e -> 1L, Long::sum);
    }
}
```

`요소`를 받아 `1L`로 변환 시킨후 더하면 됩니다.

> #### 제네릭 와일드카드 '?' 사용법
>
> 위의 예제에서 `?`는 `Collector`의 형식이 알려지지 않았음을 의미합니다. 즉 누적자의 형식이 자유롭습니다.

#### 자신의 상황에 맞는 최적의 해법 선택

하나의 연산을 다영한 방법으로 해결할 수 있음을 위의 예제들을 통해 배웠습니다.

또한, `Stream`에서 제공하는 메소드를 이용하는 것에 비해 `Collector`를 이용하는 코드가 더 복잡한 대신
`재사용성`과 `커스터마이즈 가능성`을 제공하여 높은 수준의 `추상화`와 `일반화`를 얻을 수 있습니다.

문제를 해결할 수 있는 다양한 해결 방법을 확인 후, 가장 일반적으로 문제에 특화된 해결책을 고르는 것이 바람직합니다.

위에서 요리의 총 칼로리를 구하는 로직은 제일 마지막에 작성한 로직이 `가독성`과 `성능적인 측면`에서 가장 바람직합니다.

```java
class Foo {
    public static void main(String[] args) {
        int totalCalories4 = menu.stream()
                .mapToInt(Dish::getCalories)
                .sum();
    }
}
```

## 6.3 그룹화

데이터 집합을 하나 이상의 특성으로 분류해서 `그룹화`하는 연산도 `DB`에서 많이 수행되는 작업입니다.

`명령형`으로 `그룹화`를 구현하면 까다롭고, 할일이 많으며, 에러도 많이 발생하는 반면,
`함수형`을 이용하면 `가독성` 있는 한 줄의 코드로 `그룹화`를 구현할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, List<Dish>> dishesByType = menu.stream().collect(groupingBy(Dish::getType));
    }
}
```

`Dish.Type`과 일치하는 모든 요리를 추출하는 함수를 `groupingBy` 메소드로 전달했습니다. 이 함수를 기준으로 `그룹화`되므로 이를 `분류 함수`라고 합니다.

예를 들어, 400칼로리 이하는 `diet`, 400 ~ 700칼로리는 `normal`, 700칼로리 이상은 `fat`로 분류한다고 하면 아래처럼 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<CaloricLevel, List<Dish>> dishesByCaloricLevel = menu.stream().collect(
                groupingBy(
                        dish -> {
                            if (dish.getCalories() <= 400) return CaloricLevel.DIET;
                            else if (dish.getCalories() <= 700) return CaloricLevel.NORMAL;
                            else return CaloricLevel.FAT;
                        }
                )
        );
    }
}
```

### 6.3.1 그룹화된 요소 조작

500칼로리가 넘는 요리만 `filter`한다고 했을 때, 아래처럼 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, List<Dish>> caloricDishesByType = menu.stream()
                .filter(dish -> dish.getCalories() > 500)
                .collect(groupingBy(Dish::getType));

        // {OTHER=[french fries, pizza], MEAT=[pork, beef]}
    }
}
```

하지만, 위의 로직의 경우 `filter`를 먼저 하기 때문에, 특정 타입이 하나도 500칼로리를 넘지 않는다면 `grouping`될 때 제외가 되어버립니다.

이 문제를 해결하기 위해 `Collector`은 두 번째 인수를 갖도록 `groupingBy` 메소드를 `override`하여 제공합니다. 두 번째 인수로 `filter Predicate`를 이동시킴으로써 위의
문제를 해결할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, List<Dish>> caloricDishesByType2 = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                filtering(dish -> dish.getCalories() > 500, toList())
                        )
                );

        // {OTHER=[french fries, pizza], FISH=[], MEAT=[pork, beef]}
    }
}
```

만약 `Dish`대신 다른 값으로 변환하고 싶다면 `mapping`함수를 사용할 수 있습니다. `flatMapping`도 지원합니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, List<String>> dishNamesByType = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                mapping(Dish::getName, toList())
                        )
                );
    }
}
```

### 6.3.2 다수준 그룹화

두 인수를 받는 `groupingBy` 메소드는 일반적인 `분류 함수`와 `Collector`를 인수로 받아 `다수준`으로 `그룹화`를 할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Map<CaloricLevel, List<Dish>>> dishesByTypeCaloricLevel = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                groupingBy(
                                        dish -> {
                                            if (dish.getCalories() <= 400) return CaloricLevel.DIET;
                                            else if (dish.getCalories() <= 700) return CaloricLevel.NORMAL;
                                            else return CaloricLevel.FAT;
                                        }
                                )
                        )
                );
    }
}
```

위의 예제는 두 수준으로 구현했지만, 계속 해서 `groupingBy`를 사용함으로 `n 수준 트리구조`로 구현할 수 있습니다.

### 6.3.3 서브그룹으로 데이터 수집

`분류 함수` 한 개의 인수를 갖는 `groupingBy(f)`는 `grouping(f, toList())`의 축약형 입니다.

즉, `filter`, `mapping`, `groupingBy` 외에도 다양한 `Collector`를 적용할 수 있습니다.

- `Dish.Type` 별 **개수**

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Long> typesCount = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                counting()
                        )
                );
    }
}
```

- `Dish.Type` 중 **칼로리가 가장 높은 요리**

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Optional<Dish>> mostCaloricByType = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                maxBy(comparingInt(Dish::getCalories))
                        )
                );
    }
}
```

#### 컬렉터 결과를 다른 형식에 적용하기

`Colletors.colletingAndThen` 팩토리 메소드를 이용하면 `Collector`가 반환한 결과를 다른 형식으로 변환할 수 있습니다.

다음처럼 위의 예제에서 칼로리가 가장 높은 요리의 경우 `Optional`로 감싸져있는데 모두 `Optional`에서 꺼낸 값을 반환받도록 할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Dish> mostCaloricByType2 = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                collectingAndThen(
                                        maxBy(comparingInt(Dish::getCalories)),
                                        Optional::get
                                )
                        )
                );
    }
}
```

`cpllectingAndThen` 메소드는 적용할 `Collector`와 `변환 함수`를 인수로 받아 다른 `Collector`를 반환합니다. 반환되는 `Collector`는 기존`Collector`의 래퍼 역할을
하며 `collect` 마지막 과정에서 `변환 함수`로 자신이 반환하는 값을 `매핑`합니다.

> `reducing Collectr`는 절대 `Optional.empty()`를 반환하지 않으므로 위의 로직은 안전한 로직입니다.

- `groupingBy`는 요리의 종류에 따라 메뉴 `Stream`을 `그룹화` 합니다.
- `collectingAndThen` 메소드는 위에서 `그룹화` 된 `서브스트림`에 적용됩니다.
- `collectingAndThen` `Collector`는 세 번째 `Collector`를 감쌉니다.
- `reducing Collector`가 `서브스트림`에 연산을 수행한 결과에 `collectingAndThen`의 `반환 함수`를 적용합니다.

#### groupingBy와 함께 사용하는 다른 컬렉터 예제

- `summingInt`를 활용한 그룹별 총 합계

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Integer> totalCaloriesByType = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                summingInt(Dish::getCalories)
                        )
                );
    }
}
```

- `mapping`

`mapping`은 `Stream` 인수를 `변환하는 함수`와 결과 객체를 누적하는 `Collector`를 인수로 받습니다.

아래는 각 `Type` 별로 존재하는 `CaloricLevel`을 추출하는 로직입니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Set<CaloricLevel>> caloricLevelsByType = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                mapping(
                                        dish -> {
                                            if (dish.getCalories() <= 400) return CaloricLevel.DIET;
                                            else if (dish.getCalories() <= 700) return CaloricLevel.NORMAL;
                                            else return CaloricLevel.FAT;
                                        },
                                        toSet()
                                )
                        )
                );
    }
}
```

위의 예제에서는 `Set`의 형식이 정해져있지 않습니다. `toCollection`을 이용하면 원하는 방식으로 결과를 제어할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Dish.Type, Set<CaloricLevel>> caloricLevelsByType2 = menu.stream()
                .collect(
                        groupingBy(
                                Dish::getType,
                                mapping(
                                        dish -> {
                                            if (dish.getCalories() <= 400) return CaloricLevel.DIET;
                                            else if (dish.getCalories() <= 700) return CaloricLevel.NORMAL;
                                            else return CaloricLevel.FAT;
                                        },
                                        toCollection(HashSet::new)
                                )
                        )
                );
    }
}
```

## 6.4 분할

`분할`은 `분할 함수`라 불리는 `Predicate`를 `분류 함수`로 사용하는 특수한 `그룹화` 기능입니다.

`Predicate`는 `boolean`을 반환하므로 `Map`은 최대 두 개의 그룹으로 분류됩니다.

예를 들어, 모든 요리를 채식 요리와 채식이 아닌 요리로 분류한다고 하면 아래와 같이 작성할 수 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Boolean, List<Dish>> partitionedMenu = menu.stream()
                .collect(
                        partitioningBy(
                                Dish::isVegetarian
                        )
                );

        partitionedMenu.get(true); // 모든 채식 요리
        partitionedMenu.get(false); // 모든 채식이 아닌 요리
    }
}
```

### 6.4.1 분할의 장점

`분할 함수`가 반환하는 `true`, `false` 두 가지 요소의 `Stream` 리스트를 모두 유지한다는 것이 분할의 장점입니다.

또한, `Collector`를 두 번째 인수로 전달할 수 있는 `override`된 `partitioningBy` 메소드도 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Boolean, Map<Dish.Type, List<Dish>>> vegetarianDishesByType = menu.stream()
                .collect(
                        partitioningBy(
                                Dish::isVegetarian,
                                groupingBy(Dish::getType)
                        )
                );
        // {false={FISH=[prawns, salmon], MEAT=[pork, beef, chicken]}, true={OTHER=[french fries, rice, season fruit, pizza]}}
    }
}
```

이를 응용하여 채식 요리와 채식이 아닌 요리 중 가장 칼로리가 높은 요리만 추출할 수도 있습니다.

```java
class Foo {
    public static void main(String[] args) {
        Map<Boolean, Dish> mostCaloricPartitionedByVegetarian = menu.stream()
                .collect(
                        partitioningBy(
                                Dish::isVegetarian,
                                collectingAndThen(
                                        maxBy(comparingInt(Dish::getCalories)),
                                        Optional::get
                                )
                        )
                );
        // {false=pork, true=pizza}
    }
}
```

`partitioningBy`가 반환한 `Map`은 `true`, `false`만 포함하므로 간결하고 효과적입니다. 내부적으로는 `특수한 Map`과 두 개의 `필드`로 구현되었습니다.

`groupingBy`에서 다수준으로 `그룹화` 했던 것처럼 `partitioningBy`로 다수준 `분할`도 가능합니다.

### 6.4.2 숫자를 소수와 비소수로 분할하기

정수 `n`을 인수로 받아서 `2`에서 `n`까지의 자연수를 `소수`와 `비소수`로 나눠보겠습니다.

```java
class Partitioning {
    public static void main(String[] args) {
        int n = 10000;
        Map<Boolean, List<Integer>> partitionPrimes = IntStream.rangeClosed(2, n)
                .boxed()
                .collect(partitioningBy(Partitioning::isPrime));
    }

    public static boolean isPrime(int candidate) {
        return IntStream.rangeClosed(2, (int) Math.sqrt(candidate))
                .noneMatch(n -> candidate % n == 0);
    }
}
```

## 6.5 Collector 인터페이스

`interface Collector` 는 `reducing 연산 (Collector)`을 어떻게 구현할지 제공하는 메소드 집합으로 구성 되어있습니다.

`interface Collector`의 시그니처와 5개의 메소드는 아래와 같습니다.

```java
class Collector {
    Supplier<A> supplier();

    BiConsumer<A, T> accumulator();

    BinaryOperator<A> combiner();

    Function<A, R> finisher();

    Set<Characteristics> characteristics();
}
```

- `T`: 수집될 `Stream` 항목의 제네릭 형식
- `A`: 누적자
- `R`: 수집 연산 결과 객체의 형식 (대개 `Collection` 형식)

예를 들어 `Stream`의 모든 요소를 `List<T>`로 수집하는 클래스를 구현한다면 아래와 같이 할 수 있습니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {}
```

누적 과정에서 사용되는 객체가 수집 과정의 최종 결과로 사용됩니다.

### 6.5.1 Collector 인터페이스의 메서드 살펴보기

`Supplier`, `BiConsumer`, `BinaryOperator`, `Function`는 `collect`에서 사용되는 반면,
`characteristics`는 `collect`가 어떤 최적화를 이용해서 `reducing 연산`을 수행할 것인지 결정하도록 돕는 `힌트 특성 집합`을 제공합니다.

#### supplier 메서드 : 새로운 결과 컨테이너 만들기

`snipplier` 메소드는 수집 과정에서 빈 누적자 인스턴스를 만드는 파라미터가 없는 함수이기 때문에 빈 결과로 이루어진 `Supplier`를 반환해야 합니다.

`ToListCollector`처럼 누적자를 반환하는 `Collector`에서는 `빈 누적자`가 비어있는 `Stream`의 수집 과정의 결과가 될 수 있습ㅂ니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {
    @Override
    public Supplier<List<T>> supplier() {
        return ArrayList::new;
    }
}
```

#### accumulator 메서드 : 결과 컨테이너에 요소 추가하기

`accumulator` 메소드는 `reducing 연산`을 수행하는 함수를 반환합니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {
    @Override
    public BiConsumer<List<T>, T> accumulator() {
        return List::add;
    }
}
```

#### finisher 메서드 : 최종 변환값을 결과 컨테이너로 적용하기

`finisher` 메소드는 `Stream` 탐색을 끝내고 누적자 객체를 최종 결과로 변환하면서 누적 과정을 끝낼 때 호출할 함수를 반환해야 합니다.

`ToListCollector` 처럼 누적자 객체가 이미 최종 `결과인 상황`에서는 변환 과정이 필요하지 않으므로 `finisher` 메소드는 `항등 함수`를 반환합니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {
    @Override
    public Function<List<T>, List<T>> finisher() {
        return Function.identity;
    }
}
```

위의 세 가지 메소드를 통해 `reducing 연산`을 만들 수 있습니다. (단, `파이프라인`과 `병렬 실행` 등은 고려하지 않음)

1. `collector.suppliter().get()`
2. `collector.accumulator().accpet(accumlator, next)`
3. `Stream`에 요소가 남아 있다면 다시 2번 진행
4. `collector.finisher().apply(accumulator)`
5. 결과 `return`

#### combiner 메소드 : 두 결과 컨테이너 병합

`combiner` 메소드는 `Stream`의 서로 다른 `서브파트`를 `병렬`로 처리할 때 누적자가 이 결과를 어떻게 처리할지 정의합니다.

`toList`의 경우 비교적 쉽게 구현할 수 있습니다. `Stream`의 `두 번째 서브파트`에서 수집한 항목 리스트를 `첫 번쨰 서브파트` 결과 리스트의 뒤에 추가 하면 됩니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {
    @Override
    public BinaryOperator<List<T>> combiner() {
        return (list1, list2) -> {
            list1.addAll(list2);
            return list1;
        };
    }
}
```

이를 이용하면 `Stream`의 `reducing`을 `병렬`로 수행할 수 있습니다.

- `Stream`을 분할해야 하는지 정의하는 조건이 `false`으로 바뀌기 전까지 재쉬적으로 분할합니다.
  (분산된 작업의 크기가 너무 작아지면 병렬 수행의 속도는 순차 수행의 속도 보다 낮아지므로, `프로세싱 코어`의 `개수`를 초과하는 병렬 작업은 효율적이지 않습니다.)
- 모든 서브스트림의 각 요소에 `reduceing 연산`을 순차적으로 적용해서 서브스트림을 `병렬`로 처리할 수 있습니다.
- 마지막으로 `combiner` 메소드가 분할된 모든 서브스트림의 결과를 합치면서 연산이 완료됩니다.

#### Characteristics 메소드

`characteristics` 메소드는 `Collector` 연산을 정의하는 `Characteristics` 형식의 `불변 집합`을 반환합니다.

`Characteristics`는 `Stream`을 `병렬`로 `reduce`할 것인지, 한다면 어떤 `최적화`를 선택할지 `힌트`를 제공합니다.

```java
enum Characteristics {
    CONCURRENT,
    UNORDERED,
    IDENTITY_FINISH
}
```

- `UNORDERED`: `reducing` 결과는 `Stream` 요소의 방문 순서나 누적 순서에 영향을 받지 않음
- `CONCURRENT`: `다중 Thread`에서 `accumlator` 함수를 동시에 호출할 수 있으며, `Stream`의 `병렬 reducing`을 수행할 수 있음
  `Collector`의 플래그에 `UNORDERED`를 함께 설정하지 않았다면, `데이터 순서가 무의미`한 상황에서만 `병렬 reducing`을 수행할 수 있습니다.
- `IDENTITY_FINISH`: `finisher` 메소드가 반환하는 함수는 단순히 `identity`를 적용할 뿐이므로 생략할 수 있습니다. 따라서 `reducing 과정`의 `최종 결과`로 `누적자 객체`를
  바로 사용할 수 있으며, `누적자 A`를 `결과 R`로 안전하게 형변환할 수 있습니다.

### 6.5.2 응용하기

위에서 공부한 내용을 바탕으로 `ToListCollector`을 만들어보면 아래와 같습니다.

```java
public class ToListCollector<T> implements Collector<T, List<T>, List<T>> {

    @Override
    public Supplier<List<T>> supplier() {
        return ArrayList::new; // 수집 연산의 시발점
    }

    @Override
    public BiConsumer<List<T>, T> accumulator() {
        return List::add; // 탐색한 항목을 누적하고 바로 누적자를 수정
    }

    @Override
    public Function<List<T>, List<T>> finisher() {
        return Function.identity(); // 항등 함수
    }

    @Override
    public BinaryOperator<List<T>> combiner() {
        return (list1, list2) -> {
            list1.addAll(list2); // 두 번째 콘텐츠아 합쳐서 첫 번째 누적자를 수정
            return list1; // 변경된 첫 번째 누적자를 반환
        };
    }

    @Override
    public Set<Characteristics> characteristics() {
        return Collections.unmodifiableSet(EnumSet.of(IDENTITY_FINISH, CONCURRENT));
        // 컬렉터의 플래그를 IDENTITY_FINISH, CONCURRENT로 설정
    }

}
```

`Collectors.toList`와 사소한 최적화를 제외하면 대체로 비슷한 로직입니다.

차이점은 `toList`는 `팩토리 메소드`인 반면, `ToListCollector`은 `new` 키워드를 통해 `인스턴스화` 한다는 점입니다.

```java
class Foo {
    public static void main(String[] args) {
        List<Dish> dishes1 = menu.stream().collect(new ToListCollector<>());
        List<Dish> dishes2 = menu.stream().collect(Collectors.toList());
    }
}
```

#### 컬렉터 구현을 만들지 않고도 커스텀 수집 수행하기

`IDENTITY_FINISH` 수집 연산에서는 `Collector` 인터페이스를 새로 구현하지 않고도 같은 결과를 만들 수 있습니다.

`Stream`은 세 함수 (`발행`, `누적`, `합침`)를 인수로 받는 `collect` 메소드를 `Override`하며 각각의 메소드는 `Collector` 인터페이스의 메소드가 반환하는 함수와 같은 기능을
수행합니다.


```java
class Foo {
    public static void main(String[] args) {
        ArrayList<Object> dishes3 = menu.stream().collect(
                ArrayList::new,
                List::add,
                List::addAll
        );
    }
}
```

위의 코드는 `간결`하지만, 기존의 코드에 비해 `가독성`이 떨어집니다. 
적절한 `class`로 `Custom class`를 구현하는 편이 `중복`을 피하고 `재사용성`을 높이는데 도움이 됩니다.

또한, `Characteristics`를 전달할 수 없기 때문에 `IDENTITY_FINISH`와 `CONCURRENT`이지만 `UNORDERED`는 아닌 `Collector`로만 동작합니다.

