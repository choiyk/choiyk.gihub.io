---
title: "Scanner"
date: 2018-10-19"
categories: Java
tags: java baekJoon-단계-1
---

## Scanner

### .next() 와 .nextLine()
* next() : can read the input only till the space. It can't read two words separated by a space. Also, next() places the cursor in the same line after reading the input.
* nextLine() : reads input including space between the words (that is, it reads till the end of line \n). Once the input is read, nextLine() positions the cursor in the next line.

### .hasNext() 와 .hasNextLine()
* hasNextLine() : Returns true if there is another line in the input of this scanner. Checks to see if there is another linePattern in the buffer.
* hasNext() : Returns true if this scanner has another token in its input. Checks if there are any more non-whitespace characters available.  
c.f) 만약, 토큰에 개행문자만 남은경우 false를 반환하지만, 개행문자는 그대로 남아있다.

### .close()
```java
Scanner scan = new Scanner(System.in);
...
scan.close(); //System.in 스트림이 함께 닫힌다.
```
* If this scanner has not yet been closed then if its underlying readable also implements the Closeable interface then the readable's close method will be invoked.  
[InputStream](https://docs.oracle.com/javase/7/docs/api/java/io/InputStream.html)은 Closeable 인터페이스를 구현한다.  
따라서, Scanner를 close()하면 InputStream도 함께 닫힌다.
* 한번이라도 Scanner가 닫히면 다시 Scanner를 쓰려 할 때 IllegalStateException이 발생한다.

## 참고자료
* Class Scanner - Java SE 9 api docs [바로가기](https://docs.oracle.com/javase/9/docs/api/java/util/Scanner.html){: .btn .btn-small}
* 콘솔 입출력 - 점프 투 자바 [바로가기](https://wikidocs.net/226){: .btn .btn--small}
* Close Scanner without closing System.in - stackoverflow [바로가기](https://stackoverflow.com/questions/14962082/close-scanner-without-closing-system-in){: .btn .btn-small}
* Scanner 에 Console 사용해서 close 후에 다시 Scanner 생성 - 블로그 [바로가기](https://blog.naver.com/shwsun/40172530715){: .btn .btn-small}
