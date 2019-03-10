---
title: 2. Kotlin 변수(Variables) 알아보기
date: 2019-03-10 15:03:86
category: kotlin
---

![](./images/kotlin-logo.png)

<br/>

> 변수(variables)는 간단히 말해서 값을 저장하는 공간입니다. 프로그래밍 언어에서 특정 계산을 수행하거나 또는 어떤 값을 저장하기 위해서
사용합니다. 이번 글에서는 Kotlin에서는 어떻게 변수를 선언하고 초기화하는지에 대해서 알아보도록 하겠습니다.

## Kotlin 변수 타입 추론
Kotlin은 강력한 타입 추론을 갖고 있습니다. 개발자가 변수의 타입을 명시적으로 선언할 수 있지만, 일반적으로 컴파일러가 변수의 타입을 추론해서
작업을 수행하게 됩니다.

### 변수 선언 및 초기화하기

```kotlin
var/val 변수명: 변수타입 = 초기화
```

<br/>

> 변수명을 식별자라고 합니다. 식별자는 키워드(var, val와 같이 Kotlin에 미리 정의된 단어)를 제외한 영문자, 숫자, 언더스코어만 가능합니다.

## var와 val 키워드는 무엇인가?
Kotlin 변수는 크게 ```mutable```와 ```immutable``` 두 가지로 나눌 수 있습니다. ```mutable```로 선언한 변수는 <b>추후에 값을 변경 할 수 있습니다.</b> 반대로 ```immutable```로 선언한 변수는 <b>초기화 이후에 값을 변경 할 수 없고 읽기만 가능합니다.</b>

프로그래밍 언어에서 값을 변경이 가능한 변수를 <b>가변 변수</b>라 부르며, Kotlin에서는 ```var``` 키워드를 사용합니다. 변경이 가능하지 않고 읽기만 가능한 변수를
<b>불변 변수</b>라 부르며, Kotlin에서는 ```val``` 키워드를 사용합니다.

```kotlin
var a: String = "initial" // 가변 변수
println(a)
val b: Int = 1 // 불변 변수
val c = 3 // 불변 변수, 타입 추론
```

```Int```는 정수(양의 정수, 0, 음의 정수) 값을 저장할 수 있는 타입입니다. Java에서는 원시 타입 ```int```를 사용했었다. Kotlin에서는 따로 원시 타입이 없고, 기본 타입들도 모두 클래스이다. 아래 Java와 Kotlin 원시 타입을 비교한 표를 참고해보자!

### Java와 Kotlin 타입

| Java   | Kotlin |
|--------|--------|
| double | Double |
| float  | Float  |
| long   | Long   |
| int    | Int    |
| short  | Short  |
| byte   | Byte   |
| string | String |

## 변수 사용 전에 반드시 초기화 해야 한다!
변수를 선언하고 사용하기 전에 반드시 초기화 작업이 선행되어야 합니다. 아래와 같은 코드를 작성하고 실행하면, ```Kotlin: Variable 'd' must be initialized``` 에러가 발생합니다. 

```kotlin
var d: Int
println(d)
```

변수를 선언하고 값을 초기화하는 방법은 여러 형태가 있습니다. 변수의 값을 첫 번째로 읽기 전에 반드시 초기화 작업이 먼저 이루어져야 한다는
것만 지키면 됩니다.

```kotlin
var a: String = "initial"
val e: Int

e = if (a == "initial") {
    1
} else {
    2
}

println(e)
```

Java에서는 따로 초기화 값을 주지 않은 기본 값을 컴파일러가 설정했지만, Kotlin에서는 명시적으로 초기화 작업을
직접 해줘야 합니다.

## 세미콜론(;)은 어디로 간건가?
Kotlin에서는 Java와 달리 문장 마지막에 ```세미콜론(;)```이 없습니다. 아예 사용하지 않는 것은 아닙니다. 예외 조건은 한 줄에 여러 문장을 적는 경우에
각 문장을 구분하기 위해서 세미콜론(;)을 사용합니다.

## 참고자료
- [Kotlin 공식 문서](https://play.kotlinlang.org/byExample/01_introduction/03_Variables)