---
title: Java 배열 원소 문자열 출력, toString() vs deepToString()
date: 2019-03-08 01:03:16
category: java
---

> 일차원 또는 다차원 배열의 원소를 문자열로 출력하는 방법에 대해 알아보겠습니다.

## Java 배열에 toString 메서드
배열의 원소 값이 어떻게 이루어졌는지 확인하기 위해서 아래 코드를 사용하면 원하는 결과 형태로 출력이 되지 않습니다. 배열의
원소가 아닌 hexadecimal 값이 출력됩니다.

```java
int[] arr = {1, 2, 3, 4, 5 };
System.out.println(arr.toString()); // hexadecimal 출력
```

<br/>

✅ 배열의 원소를 문자열로 출력하려면, ```Arrays``` 클래스의 ```toString```, ```deepToString``` 메서드를
사용해야 합니다.

## Arrays 클래스 toString, deepToString 메서드
```Arrays``` 클래스의 ```toString```과 ```deepToString``` 두 메서드 차이점으로는 N차원 배열을 다룰 수 있는지 여부입니다. toString 메서드는 일차원 배열을 출력할 때 사용하고, deepToString 메서드는 다차원 배열을 출력할 때 사용합니다.

```java
// 1차원 배열
int[] singleDimensionalArray = { 1, 2, 3, 4, 5 };

// [1, 2, 3, 4, 5]
System.out.println(Arrays.toString(singleDimensionalArray));

// 2차원 배열
int[][] multiDimensionalArray = new int[2][2];
multiDimensionalArray[0][0] = 1;
multiDimensionalArray[0][1] = 5;
multiDimensionalArray[1][0] = 30;
multiDimensionalArray[1][1] = 2;

// [[1, 5], [30, 2]]
System.out.println(Arrays.deepToString(multiDimensionalArray));
```