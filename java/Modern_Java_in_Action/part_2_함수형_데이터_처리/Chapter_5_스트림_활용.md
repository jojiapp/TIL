# Chapter 5. 스트림 활용

- [5.1 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#51-필터링)
    - [5.1.1 프레이케이트로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#511-프레이케이트로-필터링)
    - [5.1.2 고유 요소 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_5_스트림_활용.md#512-고유-요소-필터링)

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

