# Chapter 2. 동작 파라미터화 코드 전달하기

- [2.1 변화하는 요구사항에 대응하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/Chapter_2_동작_파라미터화_코드_전달하기.md#21-변화하는-요구사항에-대응하기)
    - [2.1.1 첫 번째 시도: 녹색 사과 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/Chapter_2_동작_파라미터화_코드_전달하기.md#211-첫-번째-시도--녹색-사과-필터링)
    - [2.1.2 두 번째 시도: 색을 파라미터화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/Chapter_2_동작_파라미터화_코드_전달하기.md#212-두-번째-시도--색을-파라미터화)
    - [2.1.3 세 번째 시도: 가능한 모든 속성으로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/Chapter_2_동작_파라미터화_코드_전달하기.md#213-세-번째-시도--가능한-모든-속성으로-필터링)

변화하는 요구사항은 소프트웨어 엔지니어링에서 피할 수 없는 문제입니다. 자주 변하는 요구사항에 대해 비용을 최소화 하되, 새로운 기능은 쉽게 구현할 수 있어야 장기적인 관점에서 유지보수가 쉬워집니다.

`동작 파라미터화`를 이용히면 자주 변하는 요구사항에 대응할 수 있습니다.

`동작 파라미터화`는 어떻게 실행 할 것인지 결정하지 않은 코드를 의미합니다. 예를 들어 나중에 실행될 메소드의 인수로 `코드 블록`을 전달할 수 있습니다.  
즉, `코드 블록`의 실행은 나중으로 미뤄집니다.

`Collection`을 처리할 때 아래와 같은 메소드를 구현한다고 가정합니다.

- `List`의 모든 요소에 대해서 `어떤 동작`을 수행할 수 있음
- `List` 관련 작업을 끝낸 다음에 `어떤 다른 동작`을 수행할 수 있음
- 에러가 발생하면 `정해진 어떤 다른 동작`을 수행할 수 있음

`동작 파라미터화`로 이렇게 다양한 기능을 수행할 수 있습니다.

예를 들어 룸메이트에게 식료품을 사다 달라고 부탁하는 `goAndBuy`라는 메소드가 있다고 했을 때, 어느날은 우체국에서 소포를 가져와 달라고 부탁할 수도 있습니다.

이때, 두 개를 포괄하는 `go`메소드를 만들고 원하는 동작은 `go` 메소드의 인자로 전달하여 처리할 수 있습니다.

`동작 파라미터화`를 추가하려면 쓸데 없는 코드가 늘어나지만 `Java 8`은 `Lambda expression`으로 해당 문제를 해결합니다.

## 2.1 변화하는 요구사항에 대응하기

하나의 예제를 선정한 다음 예제 코드를 점차 개선하면서 유연한 코드를 만드는 방법에 대해 알아보겠습니다.

기존의 농장 재고목록 애플리케이션에 `List`에서 `녹색 사과`만 `filtering`하는 기능을 추가한다고 가정하고 시작하면 간단한 작업이라는 생각이 들 것입니다.

### 2.1.1 첫 번째 시도 : 녹색 사과 필터링

```java
enum Color {RED, GREEN}
```

```java
class FilteringApples {
    public static List<Apple> filterGreenApples(List<Apple> inventory) {
        List<Apple> result = new ArrayList<>();
        for (Apple apple : inventory) {
            if (apple.getColor() == Color.GREEN) { // 필터링 조건
                result.add(apple);
            }
        }
        return result;
    }
}
```

`녹색 사과`만 `filtering`하는 메소드는 위 처럼 만들 수 있습니다. 이때, `빨간 사과`도 `filtering`이 하고 싶어졌다면 어떻게 고쳐야 할까요?

큰 고민 없이 메소드를 `복사`, `붙여넣기`하여 필터링 조건만 변경할 수도 있지만, 추후 더 다양한 색으로 `filtering`이 필요하다면 부적절한 방법입니다.

- 이런 경우엔 `좋은 규칙`이 하나 있습니다.

> 거의 비슷한 코드가 반복 존재한다면 그 코드를 추상화하라

### 2.1.2 두 번째 시도 : 색을 파라미터화

`filtering`할 `Color`를 파라미터로 받아 위의 문제를 해결할 수 있습니다.

```java
class FilteringApples {
    public static List<Apple> filterApplesByColor(List<Apple> inventory, Color color) {
        List<Apple> result = new ArrayList<>();
        for (Apple apple : inventory) {
            if (apple.getColor() == color) {
                result.add(apple);
            }
        }
        return result;
    }
}
```

이제 `Color`를 받아 해당 `Color`로 `filtering`할 수 있게 되었습니다.

이번엔 `무게`로도 `filtering`이 필요하다고 요구사항이 들어왔다고 하면 아래와 같이 구현할 수 있습니다.

```java
class FilteringApples {
    public static List<Apple> filterApplesByWeight(List<Apple> inventory, int weight) { // 받는 파라미터 변경
        List<Apple> result = new ArrayList<>();
        for (Apple apple : inventory) {
            if (apple.getWeight() > weight) { // 필터링 조건 변경
                result.add(apple);
            }
        }
        return result;
    }
}
```

기존의 코드를 `복사`, `붙여넣기`하여 위 처럼 만들수 있지만 이번엔 `조건`외에 모든 코드가 동일합니다.

> `복사`, `붙여넣기`는 `DRY (같은 것을 반복하지 말 것)`원칙을 어기는 일입니다.
>
> 탐색 과정을 고쳐야 하는 경우가 발생하면 메소드 전체 구현을 고쳐야 하므로 비싼 대가를 치러야 합니다.

위의 문제를 해결하기 위해 `파라미터`로 `Color`랑 `Weight`를 받고, 어떤 것으로 `filtering`할 지 `flag 파라미터`도 추가하여 처리할 수 있습니다.

### 2.1.3 세 번째 시도 : 가능한 모든 속성으로 필터링

> 해당 방식은 절대 사용하면 안됩니다.

```java
class FilteringApples {
    public static List<Apple> filterApples(List<Apple> inventory, Color color, int weight, boolean flag) { // 파라미터 추가
        List<Apple> result = new ArrayList<>();
        for (Apple apple : inventory) {
            if ((flag && apple.getColor() == color) ||
                    (!flag && apple.getWeight() > weight)) { // flag에 따른 조건
                result.add(apple);
            }
        }
        return result;
    }
}
```

아주 안좋은 코드 입니다. `flag`의 `true`, `false`가 무엇을 의미하는지도 알수 없고,
`크기`, `모양`등 `filtering`할 요구 사항이 늘어나는 경우엔 `파라미터`와 `조건`이 점점 많아질 것입니다.

요구 조건이 많아지면 지금까지 살펴 봤듯 기존에는 2가지 방법이 있습니다.

- 여러 중복된 필터 메소드 구현
- 하나의 거대한 필터 메소드 구현

> `Java 8`에서는 `동작 파라미터화`로 `filtering` 조건을 파라미터로 받아 처리할 수 있습니다.
