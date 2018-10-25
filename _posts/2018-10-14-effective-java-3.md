---
title: "규칙3 private 생성자나 enum 자료형은 싱글턴 패턴을 따르도록 설계하라"
date: 2018-10-14"
categories: EffectiveJava
tags: java singleton
---

## 규칙3
싱글턴 패턴은 private 생성자나 enum 자료형으로 설계하라
{: .notice--warning}

싱글톤(singleton)이란?  
객체를 하나만 만들 수 있는 클래스  
보통 유일할 수 밖에 없는 시스템 컴포넌트를 나타낸다.
{: .notice}

### 싱글톤을 구현하는 방법

#### 1. private 생성자의 이용
```java
public class Elvis {
  public static final Elvis INSTANCE = new Elvis(); 
  private Elvis() {...}
  ...
}
```

#### 2. static factory method 이용
```java
public class Elvis {
  private static final Elvis INSTANCE = new Elvis(); 
  private Elvis() {...} // (2)
  public static Elvis getInstance() { return INSTACE; } 
}
```

#### Lazy Initialization
```java
public class LazyInitialization {
  private static fianl LazyInitialization INSTANCE; 

  private LazyInitialization () {} 

  public static LazyInitialization getInstance (){ 
    if (INSTACE == null) return new LazyInitialization();
    return INSTACE;
  }
}
```

#### Thread Safe Initialization
```java
public class ThreadSafeInitialization {
  private static final ThreadSafeInitialization instance;

  private ThreadSafeInitialization () {} 

  public static synchronized ThreadSafeInitialization getInstance () { 
    if (instance == null) return new ThreadSafeInitialization();
    return instance;
  }
}
```

#### 3. enum 자료형의 사용
```java
public enum EnumInitialization {
  INSTACE;

  public static EnumInitialization getInstance() {
    return INSTACE;
  }
}
```

#### 4. Initialization on demand holder idiom
```java
public class InitializationOnDemandHolderIdom {
  private InitializationOnDemandHolderIdom () {} 

  private static class singletonHolder { 
    private static final InitializationOnDemandHolderIdom instance = new InitializationOnDemandHolderIdom(); 
  }

  public static InitializationOnDemandHolderIdom getInstance(){ 
    return singletonHolder.instance;
  }
}
```
현재 주로 inner class 를 이용한다. thread-safe 때문.

class는 참조되는 순간 메모리에 로딩 됨.  
class를 로딩하고 초기화하고 시점은 thread-safe를 보장한다.

## 참고자료
* static과 singleton pattern - 점프 투 자바 [바로가기](https://wikidocs.net/228){: .btn .btn--small}

규칙 4

팩토리 메소드: 특정 ㅣㄴ터페이스를 구현하는 객체ㅡㄹ 만드는 메소드

final 클래스: 클래스가 바뀌는걸 막기 위함. ??

utility class에 대해 알아보기
