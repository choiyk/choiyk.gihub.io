---
title: "규칙4 객체 생성을 막을 때는 private 생성자를 사용하라"
date: 2018-10-25"
categories: EffectiveJava
tags: java singleton
---

## 규칙4
객체 생성을 막을 때는 private 생성자를 사용하라
{: .notice--warning}

추상클래스(abstract class)  
구체적인 메소드의 내용이 존재하지 않기 때문에 인스턴스화하면 오류가 발생한다.  
따라서, 인스턴스화하려면 상속을 받아 사용해야 한다.  
즉, 추상클래스는 상속을 강제하기 위한 것이다.
{: .notice}

## 참고자료
* utility class 와 private 생성자의 사용 - 블로그 [바로가기](https://koda93.github.io/Java_private_constructor/){: .btn .btn--small}

