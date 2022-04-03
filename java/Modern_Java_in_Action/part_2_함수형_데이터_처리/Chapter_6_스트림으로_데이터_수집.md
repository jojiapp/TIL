# Chapter 6. 스트림으로 데이터 수집

- [6.1 컬렉터란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#61-컬렉터란-무엇인가)
    - [6.1.1 고급 리듀싱 기능을 수행하는 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#611-고급-리듀싱-기능을-수행하는-컬렉터)
    - [6.1.2 미리 정의된 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#612-미리-정의된-컬렉터)
- [6.2 리듀싱과 요약](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#62-리듀싱과-요약)
    - [6.2.1 스트림값에서 최댓값과 최솟값 검색](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#621-스트림값에서-최댓값과-최솟값-검색)
    - [6.2.2 요약 연산](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#622-요약-연산)
    - [6.2.3 문자열 연결](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#623-문자열-연결)
    - [6.2.4 범용 리듀싱 요약 연산](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#624-범용-리듀싱-요약-연산)

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
