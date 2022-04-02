# Chapter 6. 스트림으로 데이터 수집

- [6.1 컬렉터란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#61-컬렉터란-무엇인가)
    - [6.1.1 고급 리듀싱 기능을 수행하는 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#611-고급-리듀싱-기능을-수행하는-컬렉터)
    - [6.1.2 미리 정의된 컬렉터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_6_스트림으로_데이터_수집.md#612-미리-정의된-컬렉터)

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

