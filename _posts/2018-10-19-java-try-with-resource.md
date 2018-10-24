---
title: "Java The try-with-resources Statement"
date: 2018-10-25"
categories: Java
tags: java baekJoon-단계-1
---

## The try-with-resources Statement
The try-with-resources statement is a try statement that declares one or more resources.
A resource is an object that must be closed after the program is finished with it.
The try-with-resources statement ensures that each resource is closed at the end of the statement.
Any object that implements java.lang.AutoCloseable, which includes all objects which implement java.io.Closeable, can be used as a resource.

ex) Scanner, BufferedReader, Statement ...

#### AutoCloseable 인터페이스
```java
/**
 * @author Josh Bloch
 * @since 1.7
 */
public interface AutoCloseable {
    void close() throws Exception;
}
```
JDK1.7에 추가

#### try-with-resource Statement 사용법
```java
static String readFirstLineFromFile(String path) throws IOException {
    try (BufferedReader br = new BufferedReader(new FileReader(path))) {
        return br.readLine();
    } catch(...){
      ...
    }
}
```
* try(){} 형태로 사용이 가능하며 () 안에 들어올 수 있는건 AutoCloseable 구현체뿐이다.
* 기존 try 블록처럼 catch, finally 블록을 사용할 수 있다.

#### try-with-resources with Multiple Resources
```java
try (InputStream in = new FileInputStream(inFile);
     OutputStream out = new FileOutputStream(outFile)) {
    ...
} catch(IOException ex) {
    ...
}
// in과 out 모두 자동으로 종료됨
```

### 참고자료
* The try-with-resources Statement - Java Tutorials [바로가기](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html){: .btn .btn-small}
* 중첩 try-with-resource는 어떻게 작동할까? - 블로그 [바로가기](http://multifrontgarden.tistory.com/192){: .btn .btn-small}
* Java – Try with Resources - Baeldung [바로가기](https://www.baeldung.com/java-try-with-resources){: .btn .btn-small}
