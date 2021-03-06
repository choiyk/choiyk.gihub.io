---
title: "규칙2 생성자 인자가 많을 때는 Builder 패턴 적용을 고려하라"
date: 2018-10-14"
categories: EffectiveJava
tags: java pattern
---

## 규칙2
생성자 인자가 많을 때는 Builder 패턴 적용을 고려하라
{: .notice--warning}

### 점층적 생성자 패턴
* 잘 동작하지만 인자 수가 늘어나면 클라이언트 코들를 작성하기 어려워지고, 무엇보다 읽기 어려운 코드가 되고 만다.

```java
// 호출 코드만으로는 각 인자의 의미를 알기 어렵다.
NutritionFacts cocaCola = new NutritionFacts(240, 8, 100, 3, 35, 27);
NutritionFacts pepsiCola = new NutritionFacts(220, 10, 110, 4, 30);
NutritionFacts mountainDew = new NutritionFacts(230, 10);
```

### 자바빈(JavaBeans) 패턴
* 1회의 함수 호출로 객체 생성을 끝낼 수 없으므로, 객체 일관성(consistency)이 일시적으로 깨질 수 있다.

객체 일관성(consistency)?
 한번 객체를 생성할때, 그 객체가 변할 여지가 존재한다는 뜻이다.
즉, set메서드는 언제 어디서든 사용 할 수 있다는 장점이 있지만, 객체의 불변성이 깨진다.
스레드 작업에 큰 단점이 될 수 있을 뿐더러, 컴파일러 오류는 아니지만, 우리가 원하지 않는 결과물이 만들어 질 수 있는것이다.
{: .notice}

* 변경 불가능(immutable) 클래스를 만들 수 없다.

```java
NutritionFacts cocaCola = new NutritionFacts();
cocaCola.setServingSize(240);
cocaCola.setServings(8);
cocaCola.setCalories(100);
cocaCola.setSodium(35);
cocaCola.setCarbohdydrate(27);
```

### 빌더(Builder) 패턴
인자가 많은 생성자나 정적 팩토리가 필요한 클래스를 설계할 때, 특히 대부분의 인자가 선택적 인자인 상황에서 유용하다.

```java
NutritionFacts.Builder builder = new NutritionFacts.Builder(240, 8);
builder.calories(100);
builder.sodium(35);
builder.carbohydrate(27);
NutritionFacts cocaCola = builder.build();
```

```java
// 각 줄마다 builder를 타이핑하지 않아도 되어 편리하다.
NutritionFacts cocaCola = new NutritionFacts
    .Builder(240, 8)    // 필수값 입력
    .calories(100)
    .sodium(35)
    .carbohydrate(27)
    .build();           // build() 가 객체를 생성해 돌려준다.
```

#### 장점
* 인자에 불변식(invariant)을 적용할 수 있다.
* 빌더 객체는 여러 개의 가변인자(varargs) 인자를 받을 수 있다.
* 하나의 빌더 객체로 여러 객체를 만들 수 있다.
* 빌더 객체는 어떤 필드의 값은 자동으로 채울 수 있다.
* 인자가 설정된 빌더는 훌륭한 추상적 팩토리다.

#### 단점
* 객체를 생성하려면 우선 빌더 객체를 생성해야 하는데, 성능이 중요한 상황에서는 빌더 객체를 만드는 오버헤드가 문제가 될 수 있다.
* 점층적 생성자보다 많은 코드를 요구하기 떄문에 인자가 충분히 많은 상황(가령, 네 개 이상)에서 이용해야 한다.

## 참고자료
* 예제 코드 - 기계인간 John Grib 블로그 [바로가기](https://johngrib.github.io/wiki/builder-pattern/){: .btn .btn--small}

