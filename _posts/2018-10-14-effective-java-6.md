---
title: "규칙6 유효기간이 지난 객체 참조는 폐기하라"
date: 2018-10-25"
categories: EffectiveJava
tags: java raference gc
---

## 규칙6
유효기간이 지난 객체 참조는 폐기하라
{: .notice--warning}

### 만기 참조를 null로 만든다.
쓸 일 없는 객체 참조는 null로 만든다.

만기 참조(obsolete reference)란,  
다시 이용되지 않을 참조(reference)를 말한다.
{: .notice}

간단한 스택(Stack) 구현 사례를 보자.

```java
public class Stack{
  ...
  public Object pop(){
    if(size == 0)
      throw new EmptyStackException();
    return elements[--size]; 
  }
}
```
이 경우 elements 배열에서 실제로 사용되는 부분을 제외한 나머지 영역에 보관된 참조들이 만기 참조이다.

다음은 수정된 코드이다.
```java
public Object pop(){
  if(size == 0)
    throw new EmptyStackException();
  Object result = elements[--size];
  elements[size] = null; //만기 참조 제거
  return results;
}
```

#### 객체 참조를 null 처리하는 것은 규범(norm)이라기보단 예외적인 조치가 되어야 한다.

#### 자체적으로 관리하는 메모리가 있는 클래스를 만들 때는 메모리 누수가 발생하지 않도록 주의해야 한다.
ex) 스택 ...

### WeakHashMap 활용
* 캐시(Cache)
캐시 바깥에서 키를 참조하고 있을 때만 값을 보관하면 될 때 쓸 수 있도록 WeakHashMap을 가지고 캐시를 구현한다.
* 리스너(listener) 등의 역호출자(Callback)
WeakHashMap의 키로 저장하여 역호출자에 대한 약한 참조만 저장한다.

## 참고자료
* Listener 리스트를 위한 WeakHashMap 사용하기 - 블로그 [바로가기](http://egloos.zum.com/folog/v/1237140){: .btn .btn--small}
* Java Reference와 GC - Naver D2 [바로가기](https://d2.naver.com/helloworld/329631){: .btn .btn--small}
