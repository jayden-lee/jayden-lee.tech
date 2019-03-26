---
title: Effective Java 아이템 10. equals는 일반 규약을 지켜 재정의하라
date: 2019-03-26 21:03:95
category: java
---

> Effective Java 3판을 학습하며 요약한 내용입니다. 자세한 내용은 책을 참고해주시기 바랍니다.

```equals``` 메서드는 재정의하기 쉬워 보이지만 잘못된 재정의를 통해 프로그램 오류를 일으킬 수 있다. 이러한 문제를 회피하기 위한 가장 좋은 방법은 아예 재정의를 하지 않는 것이다. 그냥 두면 해당 인스턴스는 오직 자기 자신과만 같게 된다. 

## equals 재정의 하기전 확인해야 할 사항
다음과 같은 조건 중 하나에 해당한다면 ```equals``` 메서드를 재정의하지 않는 것이 최선이다.

1. 각각의 객체가 본질적으로 고유하다.
2. 클래스에 논리적 동일성 검사 방법이 필요하지 않다.
3. 상위 클래스에서 재정의한 equals가 하위 클래스에서도 사용하기에 적당하다.
4. 클래스가 private 또는 package-private로 선언되어 있으며, equals 메서드를 호출할 일이 없다.

## equals를 재정의해야 하는 경우
객체 동일성이 아닌 논리적 동일성의 개념을 지원하는 클래스의 경우 또는 상위 클래스의 equals가 논리적 동치성을 비교하도록 구현 되어 있지 않은 경우에 재정의해야 한다.

## equals 재정의 일반 규약
equals 메서드는 동치관계(equivalence relation)을 구현한다. equals를 메서드를 정의해야 하는 일반 규약은 다음과 같다.

1. 반사성 : null이 아닌 참조 x가 있을 때, x.equals(x)는 true를 반환한다.
2. 대칭성 : null이 아닌 참조 x와 y가 있을 때, x.equals(y)는 y.equals(x)가 true이면 true를 반환한다.
3. 추이성 : null이 아닌 참조 x, y, z가 있을 때, x.equals(y)가 true이고 y.equals(z)가 true이면 x.equals(z)도 true를 반환한다.
4. 일관성 : null이 아닌 참조 x, y가 있을 때, equals를 통해 비교되는 정보에 아무 변화가 없다면, 호출 횟수에 관계 없이 x.equals(y)는 항상 같은 값을 반환한다.
5. null이 아닌 참조 x에 대해서 x.equals(null)는 항상 false를 반환한다.

## equals 메서드 구현 방법
equals 메서드 구현 방법을 각 단계별로 알아보자.

- ```==``` 연산자를 사용해 입력이 자기 자신의 참조인지 확인한다.
- ```instanceof``` 연산자로 입력이 올바른 타입인지 확인한다.
- 입력을 사용하고자 하는 타입으로 형변환한다.
- 입력 객체와 자기 자신의 핵심 필드들이 모두 일치하는지 하나씩 검사한다.

<br/>

다음 코드는 equals 메서드를 구현한 예제이다.

```java
public final class PhoneNumber {
    private final short areaCode, prefix, lineNum;

    // 생성자 생략...

    @Override
    public boolean equals(Object o) {
        if (o == this) {
            return true;
        }

        if(!(o instanceof PhoneNumber)) {
            return false
        }

        PhoneNumber phoneNumber = (PhoneNumber) o;
        return phoneNumber.lineNum == this.lineNum
            && phoneNumber.prefix = this.prefix
            && phoneNumber.areaCode = this.areaCode;
    }
}
```

## 마지막 주의 사항
- equals 메서드를 재정의할 때는 ```hashcode```도 반드시 재정의하자 ([item 11 참고](https://jayden-lee.tech/java/effective-java-item11/))
- 너무 복잡하게 해결하려고 하지 말자
- Object 타입이 아닌 매개변수를 받는 equals 메서드를 선언하지 말자

## 결론
equals를 구현해야 한다면 직접 하기보다는 [AutoValue 프레임워크](https://github.com/google/auto/tree/master/value)를 이용해보자. 클래스에 어노테이션만 추가하면 프레임워크가 알아서 equals 메서드를 작성해준다. 직접 구현해도 상관 없다. 다만, 위에서 살펴본 규약을 잘 지켜야 한다는 것이 문제이다.

## 이해가 안된다면 아래 자료를 추가적으로 살펴보자
- [리스코프 치환 원칙](http://wonwoo.ml/index.php/post/1780)
- [google AutoValue](https://github.com/google/auto/blob/master/value/userguide/index.md)
- [why autovalue?](https://www.baeldung.com/introduction-to-autovalue)
- [autovalue plugin youtube](https://www.youtube.com/watch?v=sMX9PT3ecu8)
- [lombok - @EqualsAndHashCode](https://projectlombok.org/features/EqualsAndHashCode)