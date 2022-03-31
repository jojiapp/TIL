# Chapter 6. 스트림으로 데이터 수집

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
