# Chapter 4. 스트림 소개

- [4.1 스트림이란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_4_스트림_소개.md#41-스트림이란-무엇인가)
- [4.2 스트림 시작하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_2_함수형_데이터_처리/Chapter_4_스트림_소개.md#42-스트림-시작하기)

거의 모든 `Java Application`은 `Collection`을 만들고 처리하는 과정을 포함합니다.

`Collection`으로 데이터를 그룹화하거나, `Collection`을 반복하면서 특정 값을 더하는 등의 처리를 할 수 있습니다. 하지만, 아직 완벽한 `Collection` 관련 연산을 지원하려면 한참
멀었습니다.

예를 들어, 요리 관련 `Application`이 있다고 할 때, 대부분의 비즈니스 로직은 카테고리로 `그룹화`를 하거나 `가장 비싼 요리`를 찾는 등의 `연산`이 포함됩니다.  
대부분의 `Database`에서는 `SELECT name FROM dishes WHERE calorie < 400`처럼 `선언형`으로 이와 같은 연산을 표현할 수 있습니다. 사용하는 입장에서는 어떻게 필터링할
것인지는 구현할 필요가 없습니다.

또한, 많은 요소를 포함하는 커다란 `Collection`의 경우 성능을 높이려면 `멀티코어 아키텍쳐`를 활용해서 `병렬`로 처리해야 합니다.  
하지만, `병렬 처리` 코드는 `단순 반복 처리` 코드에 비해 복잡하고 어렵습니다.

이와 같은 문제를 해결하기 위해 `Steam`이 등장 했습니다.

## 4.1 스트림이란 무엇인가?

`Stream`은 `Java 8`에 추가된 새로운 기능입니다.

`Stream`을 이용하면 `선언형`으로 `Collection` 데이터를 처리할 수 있습니다. 또한, `멀티스레드 코드`를 구현하지 않아도 데이터를 `투명하게` `병렬`로 처리할 수 있습니다.

예를 들어, 저칼로리 요리명을 반환하고, 칼로리를 기준으로 요리를 정렬하는 로직을 `Java 7`에서는 아래와 같이 작성합니다.

```java
class Foo {
    public static void main(String[] args) {
        // 저칼로리 요리 추출
        List<Dish> lowCaloricDishes = new ArrayList<>();
        for (Dish dish : menu) {
            if (dish.getCalories() < 400) {
                lowCaloricDishes.add(dish);
            }
        }
        // 칼로리 기준 정렬
        Collections.sort(lowCaloricDishes, new Comparator<Apple>() {
            @Override
            public int compare(Dish dish1, Dish dish2) {
                return Integer.compare(dish1.getCalories(), dish2.getCalories());
            }
        });
        // 요리 이름 선택
        List<String> lowCaloricDishNames = new ArrayList<>();
        for (Dish dish : lowCaloricDishNames) {
            lowCaloricDishNames.add(dish.getName());
        }
    }
}
```

위의 예제에서는 `lowCaloricDishes`라는 `컨테이너 역할`만 하는 `가비지 변수`를 사용했습니다.
`Java 8`에서는 이러한 `세부 구현`을 라이브러리 내에서 모두 처리 합니다.

아래는 `Java 8`의 `Stream`을 이용한 방법입니다.

```java
class Foo {
    public static void main(String[] args) {
        List<String> lowCaloricDishNames = menu.stream()
                .filter(d -> d.getCalories() < 400)
                .sorted(comparing(Dish::getCalories))
                .map(Dish::getName)
                .collect(toList());
    }
}
```

위의 로직에서 `stream()`을 `parallelStream()`으로 변경하면 `멀티코어 아키텍처`에서 `병렬`로 실행할 수 있습니다.

`Stream`으로 코드를 구현하면 다음과 같은 장점이 있습니다.

- `선언형`으로 코드를 구현
    - `세부 구현`은 하지 않고 **저칼로리의 요리만 선택하라** 같은 동작의 수행을 지정할 수 있습니다.
    - `동작 파라미터화`를 활용하면 저칼로리 대신 고칼로리로 요구사항이 변경되어도 대응하기가 쉽습니다.
- `가독성`
    - 여러 연산을 `Pipeline`으로 연결해도 여전히 `가독성`과 `명확성`이 유지됩니다.
- `조립할 수 있음`
    - `유연성`이 더 좋아집니다.
- `병렬화`
    - 성능이 좋아집니다.

`filter`, `sorted`, `map`, `collect` 같은 연산은 `고수준 빌딩 블록`으로 이루어져 있어, 특정 `스레딩 모델`에 제한되지 않고 어떤 상황에서든 사용할 수 있습니다. 또한, 멀티코어
아키텍처를 최대한 `투명하게 활용`할 수 있게 구현되어 있습니다.

즉, `데이터 처리 과정`을 `병렬화` 하면서 `스레드`와 `락`을 걱정할 필요가 없어집니다.

> `구글`에서 만든 `구아바`, `아파치 공통 컬렉션 라이브러리`, `마리오 푸스코`가 만든 `람다제이` 같은 `기타 라이브러리`도 있습니다.

## 4.2 스트림 시작하기

`Java 8`에는 `stream` 메소드가 추가 되었습니다. `(java.util.stream.Stream 참고)`

`숫자 범위`나 `I/O`자원에서 `Stream` 요소를 만드는 등 `stream` 메소드 외에도 다양한 방법으로 `Stream`을 만들 수 있습니ㅣ다.

> `Stream`이란 **데이터 처리 연산을 지원하도록 소스에서 추출된 연속된 요소** 입니다.

### Stream 특징

#### 연속된 요소

- `Collection`과 마찬가지로 특정 요소 형식으로 이루어진 `연속된 값 집합`의 `interface`를 제공합니다.
- `Collection`은 요소 `저장` 및 `접근 연산`이 주를 이루는 반면, `Stream`은 `표현 계산식`이 주를 이룹니다.
- 즉, `Collection`의 주제는 `데이터`이고, `Stream`의 주제는 `계산`입니다.

#### 소스

- `Collection`, `Array`, `I/O` 자원 등의 데이터 제공 소스로 부터 데이터를 소비하기 때문에, 정렬된 `Collection`으로 부터 `Stream`을 생성하면 정렬이 그대로 유지됩니다.

#### 데이터 처리 연산

- `함수형 프로그래밍`에서 일반적으로 지원하는 연산 및 `Database`와 비슷한 연산을 지원합니다.
- `순차적` 또는 `병렬`로 실행할 수 있습니다.

#### 파이프라이닝

- 대부분의 `Stream` 연산은 `Stream` 연산끼리 연결하여 커다란 `Pipeline`을 구성할 수 있도록 `Stream`자신을 `반환`합니다.
- 그 덕에 `laziness`, `short-circuiting`같은 최적화도 얻을 수 있습니다.

#### 내부 반복

- `Collection` 처럼 반복자를 이용하여 `명시적으로 반복`하는 것과 달리 `내부 반복`을 지원합니다.
