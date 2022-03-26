# Modern Java in Action

## Part 1. 기초

### [Chapter 1. 자바 8, 9, 10, 11 무슨 일이 일어나고 있는가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md)

- [1.1 역사의 흐름은 무엇인가](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#11-역사의-흐름은-무엇인가)
- [1.2 왜 아직도 자바는 변화하는가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#12-왜-아직도-자바는-변화하는가)
    - [1.2.1 왜 아직도 자바는 변화하는가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#121-프로그래밍-언어-생태계에서-자바의-위치)
    - [1.2.2 스트림 처리](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#122-스트림-처리)
    - [1.2.3 동작 파라미터화로 메서드에 코드 전달하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#123-동작-파라미터화로-메서드에-코드-전달하기)
    - [1.2.4 병렬성과 공유 가변 데이터](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#124-병렬성과-공유-가변-데이터)
    - [1.2.5 자바가 진화해야 하는 이유](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#125-자바가-진화해야-하는-이유)
- [1.3 자바 함수](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#13-자바-함수)
    - [1.3.1 메서드와 람다를 일급 시민으로](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#131-메서드와-람다를-일급-시민으로)
    - [1.3.2 코드 넘겨주기 : 예제](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#132-코드-넘겨주기--예제)
    - [1.3.3 메서드 전달에서 람다로](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#133-메서드-전달에서-람다로)
- [1.4 스트림](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#14-스트림)
    - [1.4.1 멀티스레딩은 어렵다](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#141-멀티스레딩은-어렵다)
- [1.5 디폴트 메서드와 자바 모듈](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#15-디폴트-메서드와-자바-모듈)
- [1.6 함수형 프로그래밍에서 가져온 다른 유용한 아이디어](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#16-함수형-프로그래밍에서-가져온-다른-유용한-아이디어)
- [1.7 마치며](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_1_자바_8_9_10_11_무슨_일이_일어나고_있는가.md#17-마치며)

### [Chapter 2. 동작 파라미터화 코드 전달하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md)

- [2.1 변화하는 요구사항에 대응하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#21-변화하는-요구사항에-대응하기)
    - [2.1.1 첫 번째 시도: 녹색 사과 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#211-첫-번째-시도--녹색-사과-필터링)
    - [2.1.2 두 번째 시도: 색을 파라미터화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#212-두-번째-시도--색을-파라미터화)
    - [2.1.3 세 번째 시도: 가능한 모든 속성으로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#213-세-번째-시도--가능한-모든-속성으로-필터링)
- [2.2 동작 파라미터화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#22-동작-파라미터화)
    - [2.2.1 네 번째 시도 : 추상적 조건으로 필터링](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#221-네-번째-시도--추상적-조건으로-필터링)
- [2.3 복잡한 과정 간소화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#23-복잡한-과정-간소화)
    - [2.3.1 익명 클래스](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#231-익명-클래스)
    - [2.3.2 다섯 번째 시도 : 익명 클래스 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#232-다섯-번째-시도--익명-클래스-사용)
    - [2.3.3 여섯 번째 시도 : 람다 표현식 사용](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#233-여섯-번째-시도--람다-표현식-사용)
    - [2.3.4 일곱 번째 시도 : 리스트 형식으로 추상화](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#234-일곱-번째-시도--리스트-형식으로-추상화)
- [2.4 실전 예제](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#24-실전-예제)
    - [2.4.1 Comparator로 정렬하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#241-Comparator로-정렬하기)
    - [2.4.2 Runnable로 코드 블록 실행하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#242-Runnable로-코드-블록-실행하기)
    - [2.4.3 Callable을 결과로 반환하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#243-Callable을-결과로-반환하기)
    - [2.4.4 GUI 이벤트 처리하기](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#244-GUI-이벤트-처리하기)
- [2.5 마치며](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_2_동작_파라미터화_코드_전달하기.md#25-마치며)

### [Chapter 3. 람다 표현식](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md)

- [3.1 람다란 무엇인가?](https://github.com/jojiapp/TIL/blob/master/java/Modern_Java_in_Action/part_1/Chapter_3_람다_표현식.md#31-람다란-무엇인가)