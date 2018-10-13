---
title: "Effective Java 규칙1"
date: 2018-10-14"
categories: EffectiveJava
tags: java
---

## 규칙1
생성자 대신 정적 팩토리 메소드를 사용할 수 없는지 생각해 보라
{: .notice--warning}

### 정적 팩토리 메소드
Static Factory Method 는 public static method 로서 외부 클래스에서 바로 접근할 수 있는 method 로, 생성자의 역할을 한다.

### 장점
* 생성자와는 달리 정적 팩토리 메소드는 이름이 있다.
  같은 시그너처를 갖는 생성자를 여러 개 정의할 필요가 있을 때 그 생성자를 정적 팩토리 메소드로 바꾼다.
* 호출할 때마다 새로운 객체를 생성할 필요가 없다.
* 하위 자료형 객체를 반환할 수 있다.

### 단점
* 정적 팩토리 메서드만 있는 클래스라면, 생성자가 없으므로 하위 클래스를 못 만든다.
* 정적 팩토리 메서드는 다른 정적 메서드와 잘 구분되지 않는다. (문서만으로 확인하기 어려울 수 있음)
주석을 통해 정적 팩토리 메소드임을 알리거나, 정적 팩토리 메소드 이름을 지을 때 조심하는 수밖에 없다.

### 참고자료
* 예제 코드 - 기계인간 John Grib 블로그 [바로가기](https://johngrib.github.io/wiki/static-factory-method-pattern/){: .btn .btn--small}
* static과 singleton pattern - 점프 투 자바 [바로가기](https://wikidocs.net/228){: .btn .btn--small}
* 정적 메소드로만 구성된 Collections Class [바로가기](http://www.incodom.kr/Java/java.util.Collections){: .btn .btn--small}
