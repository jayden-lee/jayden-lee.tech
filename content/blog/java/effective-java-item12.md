---
title: Effective Java 아이템 12. toString을 항상 재정의하라
date: 2019-03-27 00:03:83
category: java
---

> Effective Java 3판을 학습하며 요약한 내용입니다. 자세한 내용은 책을 참고해주시기 바랍니다.

## toString 메서드
```java.lang.Object``` 클래스가 ```toString``` 메서드가 제공하지만, 해당 메서드를 호출하면 반환되는 문자열은 사용자가 보고 싶어하는 문자열 값 형태가 아니다. 값은 클래스의 이름과 @ 문자 기호와 16진수로 표현된 해시 코드가 붙은 문자열이 반환된다.

다음 코드는 toString 구현하지 않은 클래스의 toString 메서드를 호출하는 예제이다.

```java
public class Main {
	public static void main(String[] args) {
		Product product = new Product(1, "Toy");

        // ch10.Product@70dea4e 출력
		System.out.println(product);
	}
}
```

toString 메서드의 일반 규약으로는 반환되는 문자열이 "사람에게 읽기 쉽도록 간략하지만 유용한 정보를 제공해야 된다." 라고 명시되어 있다. 모든 하위 클래스에서는 toString 메서드를 재정의하는 것이 바람직하다. 이전에 살펴본 equals, hashCode 규약을 지키는 것보다 덜 중요하지만, toString 메서드의 재정의를 잘 해놓는다면 클래스를 좀 더 좋게 사용할 수 있다. 예를 들어 디버깅 또는 로깅 할 때 해당 객체의 정보를 쉽게 파악 할 수 있다.

## toString 메서드 재정의
toString 메서드는 객체 내에 중요 정보를 전부 담아서 문자열로 반환해야 한다. 예를 들어 전화번호부 클래스 PhoneNumber가 있다면, 전화번호부에 관련된 정보를 전달해야 한다. 필드가 많아서 문자열로 변환하기가 까다롭다면 요약한 정보를 반환해도 된다.

다음 코드는 PhoneNumber 클래스에서 toString 메서드를 재정의한 예제이다.

```java
@Override
public String toString() {
    return String.format("%03d-%03d-%04d",
            areaCode, prefix, lineNum);
}
```

toString 결과 형식을 포맷팅 해서 반환하게 되면, 이를 이용하는 클라이언트 또는 다른 로직이 있을 수 있다. toString 메서드에서 반환되는 문자열을 파싱해서 데이터를 사용하려고 하는데, 해당 값이 변화 한다면 관련된 로직들 모두 매번 변경되어야 한다. toString 메서드에 주석으로 "형식이 변화할 수 있다는 것"을 명시해야 한다. 그리고 되도록이면 toString 반환 값을 이용하여 로직을 작성하는 것은 바람직하지 않다.

toString에 포함되는 정보는 다른 API를 통해 가져갈 수 있도록 각 필드의 getter 메서드를 제공해야 한다. 클래스의 정보를 필요로 하는 개발자들은 굳이 toString 정보를 파싱할 필요 없이 각 필드를 접근할 수 있는 API를 통해 정보를 얻을 수 있다.

## 결론
모든 구체 클래스에서 Object의 toString 메서드를 재정의하자. 상위 클래스에서 이미 알맞게 구현했다면 생략해도 된다. toString을 재정의하면, 디버깅 또는 로깅할 때 유용하다. 그리고 해당 객체의 유용한 정보를 파악할 수 있다.