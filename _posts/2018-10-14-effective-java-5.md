---
title: "규칙5 불필요한 객체는 만들지 말라"
date: 2018-10-25"
categories: EffectiveJava
tags: java
---

## 규칙5
불필요한 객체는 만들지 말라
{: .notice--warning}

### 기능적으로 동일한 객체는 필요할 때마다 만드는 것보다 재사용하는 편이 낫다.

#### 변경 불가능 객체

* 변경 불가능(immutable) 객체는 언제나 재사용할 수 있다.

```java
String a = "abc"; 
String b = "abc";
System.out.println(a == b);  // true

String c = new String("abc");
String d = new String("abc");
System.out.println(c == d);  // false
```

`String a = "abc"; ` 이렇게 하면 실행할 때마다 객체를 만드는 대신, 동일한 String 객체를 사용한다. 

* 생성자와 정적 팩토리 메소드를 함께 제공하는 변경 불가능 클래스의 경우, 생성자`Boolean(String)` 대신 정적 팩토리 메소드`Boolean.valueOf(String)`를 이용하면 불필요한 객체 생성을 피할 수 있을 때가 많다.  

#### 변경 가능한 객체
* 변경할 일이 없다면 변경 가능한 객체도 재사용할 수 있다.  
ex) 값을 바꿀 일이 없는 변경 가능한 객체(Date)를 static final 필드로 바꾸고, 정적 초기화 블록을 통해 클래스가 초기화 될 때 한 번만 만든다.
* 어댑터(adaptor)의 경우 특정 객체에 대한 어댑터를 하나 이상 만들 필요는 없다.

#### 자동 객체화(autoboxing) 주의
* 객체 표현형 대신 기본 자료형을 사용하고, 생각지도 못한 자동 객체화가 발생하지 않도록 유의하라.

### 객체를 만드는 비용이 높으니 무조건 피하라는 것이 아니라, 필요하다면 일반적으로는 만드는 것이 좋다.
* 객체를 만들어서 코드의 명확성과 단순성을 높이고 프로그램의 능력을 향상시킬 수 있다면, 일반적으로는 만드는 것이 좋다.
* 직접 관리하는 객체 풀(object pool)을 만들어 객체 생성을 피하는 기법은 객체 생성 비용이 극잔적으로 높지 않다면 사용하지 않는 것이 좋다.
* 방어적 복사가 요구되는 상황에서 객체를 재사용하는 데 드는 비용은 쓸데없이 같은 객체를 여러 벌 만드는 비용보다 훨씬 높다.

## 참고자료
* 어댑터 패턴 [바로가기](https://blog.seotory.com/post/2017/09/java-adapter-pattern){: .btn .btn--small}
