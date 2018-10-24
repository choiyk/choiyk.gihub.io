---
title: "Effective Java 규칙3"
date: 2018-10-14"
categories: EffectiveJava
tags: java
---

## 규칙3
싱글턴 패턴은 private 생성자나 enum 자료형으로 설계하라
{: .notice--warning}

현재 주로, inner class 를 이용. thread safe 떄문.

class는 참조되는 순간 메모리에 로딩 됨.
class를 로딩하고 초기화하고 시점은 thread-safe를 보장한다.

규칙 4

팩토리 메소드: 특정 ㅣㄴ터페이스를 구현하는 객체ㅡㄹ 만드는 메소드

final 클래스: 클래스가 바뀌는걸 막기 위함. ??

utility class에 대해 알아보기
