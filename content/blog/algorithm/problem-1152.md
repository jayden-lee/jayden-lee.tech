---
title: 백준 알고리즘 1152번 단어의 개수
date: 2019-03-18 00:03:23
category: algorithm
---

[1152번 단어의 개수](https://www.acmicpc.net/problem/1152) 문제는 문자열 처리 알고리즘 문제입니다.

단어 구분이 띄어쓰기만 이루어져 있으므로 문자열을 공백으로 분리한 뒤, 반복문을 통해 단어의 개수를 세면 결과값을 도출 할 수 있습니다.

한 단어가 여러 번 등장하더라도 등장한 횟수만큼 모두 세는 것이기 때문에 별다른 조건문이 필요 없습니다.

```java
import java.util.Scanner;

/**
 * 단어의 개수 문제
 * 알고리즘 분류 : 문자열 처리
 *
 * @author jayden-lee
 */
public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String text = scanner.nextLine();

        String[] splitWords = text.split(" ");

        int count = 0;

        for (String str : splitWords) {
            if (!str.isEmpty()) {
                ++count;
            }
        }

        System.out.println(count);

        scanner.close();
    }
}
```