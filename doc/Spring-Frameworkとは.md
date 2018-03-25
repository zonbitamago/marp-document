<!-- $theme: gaia -->
<!-- page_number: true -->

Spring-Frameworkとは
===

# ![](https://d1fto35gcfffzn.cloudfront.net/images/oss/spring.svg)

##### [Markdown presentation writer](https://yhatt.github.io/marp/), powered by [Electron](http://electron.atom.io/)

---

# 目次

- Spring-Frameworkとは
- Dependency Injectionとは
- AOPとは

---

# Spring-Frameworkとは

---

## Spring-Frameworkとは

The Spring Framework is divided into modules. Applications can choose which modules they need. At the heart are the modules of the core container, including a configuration model and a **dependency injection mechanism**. 


---
## Spring-Frameworkとは

Beyond that(**Dependency injection mechanism**), the Spring Framework provides foundational support for different application architectures, including messaging, transactional data and persistence, and web. It also includes the Servlet-based Spring MVC web framework and, in parallel, the Spring WebFlux reactive web framework.

---
## Spring-Frameworkとは

要約すると
- Spring-Frameworkの中核はDependency Injection
- Spring MVC等、webフレームワークの機能は周辺機能
※周辺機能は以下の通り
  - spring-webmvc: 画面遷移コントローラ
  - spring-jdbc: データアクセス
  - spring-security: 認証や権限回り
  - spring-batch: バッチ処理
 etc...

---
## Spring-Frameworkとは
<br>
更に要約すると

- Spring-Framework = Dependency Injection

<br>

#### Dependency Injection=依存性の注入??
<br>

#### ( ﾟдﾟ)ﾎﾟｶｰﾝ

---
## Dependency Injectionとは

---
## DependencyInjectionとは

###### DIのない世界

```java
public class Car {

 public void run(){
  //前準備
  Parts engine = new Engine();
  Parts gasoline = new Gasoline();
  
  //実際の実施内容
  this.engine.filled(this.gasoline);
  this.engine.startUp();
  ...
 }
}
```

---
## DependencyInjectionとは

###### DIのない世界
- 本当に記載したい内容は「実際の実施内容」
- 実施するために前準備が必要。
	- 前準備が増えていったらどうなる？？
		-　関心事(実際の実施内容)以外をたくさん記載する必要がある。
		→**関心事以外を記載すると、理解不能になりがち。。。**
        

---
## DependencyInjectionとは

###### DIのない世界
- 前準備のクラスがなかったら？？
	- コンパイルエラーが発生する。
	→**前準備のクラスが存在しないと、テストすら実施できない。。。**

---
## DependencyInjectionとは

###### DIのある世界
```xml
<!-- アノテーションでDIを行う宣言をする -->
<context:annotation-config />
<context:component-scan base-package="com.example.Car" />

```


---
## DependencyInjectionとは

###### DIのある世界

```java
public class Car {
　//前準備はDIで行う。
  @Autowired
  private Parts engine;
  @Autowired  
  private Parts gasoline;

 //関心事だけを記載することができるようになる！
 public void run(){
  
  this.engine.filled(this.gasoline);
  this.engine.startUp();
  ...
 }
}
```
---
## DependencyInjectionとは

###### DIのある世界
- 本当に記載したい内容は「実際の実施内容」
- 実施するために前準備が必要。
	- **DIを利用して、≈(実際の実施内容)以外を記載しなくて済む!**

---
## DependencyInjectionとは

###### DIのある世界
- 前準備のクラスがなかったら？？
	- 前準備のクラスがなくてもコンパイルエラーが発生しない。
	→ **テストが実行できる!**

---
## Spring-Frameworkとは

- Spring-Framework = Dependency Injection

<br>

#### Dependency Injection=依存性の注入
<br>

#### ( ･`д･´)なるほど！

---
## AOPとは

---
## AOPとは
<br>

- AOP = Aspect Oriented Programming(アスペクト指向プログラミング）
- Aspect = 横断的関心事

<br>

#### ( ﾟдﾟ)ﾎﾟｶｰﾝ

---
## AOPとは

- 実際の処理には関心事しか記載したくない。
	- 但し、実際には関心事以外も記載しなければいけない。。。
		例えば「ログ出力」
        - パフォーマンスを計測するために処理の開始、終了でログ出力を行いたい。

---
## AOPとは
```java
public class Car {
  @Autowired
  private Parts engine;
  @Autowired  
  private Parts gasoline;

 //関心事以外は書きたくない。。。
 public void run(){
  System.out.println("start!!");
  this.engine.filled(this.gasoline);
  this.engine.startUp();
  ...
  
  System.out.println("end!!");
 }
}
```

---
## AOPとは

- 実際の処理には関心事しか記載したくない。
	- 但し、実際には関心事以外も記載しなければいけない。。。
		例えば「ログ出力」
        - パフォーマンスを計測するために処理の開始、終了でログ出力を行いたい。
		→**AOPを使って関心事以外は別のメソッドとして切り出す。**

---
## AOPとは
```java
package com.car;

public class Car {
  @Autowired
  private Parts engine;
  @Autowired  
  private Parts gasoline;

 //関心事以外は別メソッドへ
 public void run(){
  this.engine.filled(this.gasoline);
  this.engine.startUp();
  ...
  
 }
}
```
---
## AOPとは
```java
@Aspect
public class LogInterceptor {
 @Before("execution(* com.car..*.*(..))")
 private void before(JoinPoint jp) {
  System.out.println("start!!");
  Object[] args = jp.getArgs();
  for (Object o : args) {
   System.out.println("Before:" + o);
  }
 }
 ...
 
}

```
---
## AOPとは
```java
@Aspect
public class LogInterceptor {
 ...
 @After("execution(* com.car..*.*(..))")
 private void after(JoinPoint jp) {
  System.out.println("end!!");
  Object[] args = jp.getArgs();
  for (Object o : args) {
   System.out.println("After:" + o);
  }
 }
}

```