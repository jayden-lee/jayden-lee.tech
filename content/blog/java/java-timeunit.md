---
title: Java TimeUnit 사용하기
date: 2019-03-07 12:03:32
category: java
---

## TimeUnit
```java.util.concurrent``` 패키지에는 Enum 자료형의 ```TimeUnit```이 있습니다. 

TimeUnit 종류는 다음과 같습니다.

- DAYS
- HOURS
- MINUTES
- MILLISECONDS
- MICROSECONDS
- NANOSECONDS

</br>

TimeUnit은 시간 데이터를 가지고 있지 않기 때문에 입력으로 시간을 나타내는 값을 넣어줘야 합니다.

```java
public enum TimeUnit {
 /**
     * Time unit representing one thousandth of a microsecond
     */
    NANOSECONDS {
        ...
    },

    /**
     * Time unit representing one thousandth of a millisecond
     */
    MICROSECONDS {
        ...
    },

    /**
     * Time unit representing one thousandth of a second
     */
    MILLISECONDS {
        ...
    },

    /**
     * Time unit representing one second
     */
    SECONDS {
        ...
    },

    /**
     * Time unit representing sixty seconds
     */
    MINUTES {
        ...
    },

    /**
     * Time unit representing sixty minutes
     */
    HOURS {
        ...
    },

    /**
     * Time unit representing twenty four hours
     */
    DAYS {
        ...
    };
}
```

## TiemUnit을 사용하여 시간 단위 변환
```TimeUnit```을 사용하면 다양한 단위로 날짜를 쉽게 표현할 수 있습니다. 시간 단위를 변환할 때, ```1 milliseconds * 1000 = 1 seconds```와 같은 코드를 작성할 필요가 없습니다.

위와 같은 코드는 시간이 흘러서 다시 보게 되면 헷갈릴 수 있습니다. 그렇기 때문에 명시적으로 표현하기 위해서는 ```TimeUnit```으로 시간 단위를 변환하는 것이 좋습니다.

```java
// SECONDS -> MILLISECONDS
long result = TimeUnit.MILLISECONDS.convert(1L, TimeUnit.SECONDS);
Assert.assertEquals(1000, result);

// MILLISECONDS -> SECONDS
long result2 = TimeUnit.SECONDS.convert(100000L, TimeUnit.MILLISECONDS);
Assert.assertEquals(100, result2);

// DAY -> SECONDS
long result3 = TimeUnit.SECONDS.convert(1L, TimeUnit.DAYS);
Assert.assertEquals(86400, result3);
```