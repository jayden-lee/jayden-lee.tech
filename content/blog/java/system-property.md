---
title: Java 시스템 속성 정보 가져오기
date: 2019-03-08 01:03:67
category: java
---

> Java에서는 시스템 속성 정보를 가져올 수 있도록 ```System``` 클래스를 제공합니다.

```System``` 클래스의 정적 메서드 ```getProperty```를 이용하면 시스템 속성 정보를 가져올 수 있습니다.
시스템 속성 종류로는 <b>OS 줄바꿈 문자, Java 버전, 사용자 작업 디렉토리, 사용자 홈 디렉토리 등</b>이 있습니다.

## 시스템 속성 값 가져오기
```System.getProperty``` 메서드의 인자로 시스템 속성의 키 값을 넘겨주면 해당하는 속성 값을 반환합니다.

```java
String value = System.getProperty("key");
```

## 시스템 프로퍼티 키 종류
| Key    | Meaning |
|--------|---------|
| file.separator | Character that separates components of a file path |
| java.class.path | Path used to find directories and JAR archives containing class files |
| java.home | Installation directory for Java Runtime Environment |
| java.vendor.url | JRE vendor URL |
| java.version | JRE version number |
| line.separator | Sequence used by operating system to separate lines in text files |
| os.arch | Operating system architecture |
| os.name | Operating system name |
| os.version | Operating system version |
| path.separator | Path separator character used in java.class.path |
| user.dir | User working directory |
| user.home | User home directory |
| user.name | User account name |


## 참고자료
- https://docs.oracle.com/javase/tutorial/essential/environment/sysprop.html