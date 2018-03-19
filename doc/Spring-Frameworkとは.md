<!-- $theme: gaia -->
<!-- page_number: true -->

Spring-Frameworkとは
===

# ![](https://d1fto35gcfffzn.cloudfront.net/images/oss/spring.svg)

##### [Markdown presentation writer](https://yhatt.github.io/marp/), powered by [Electron](http://electron.atom.io/)

---

# 目次

- Spring-Frameworkとは
- あとで書く

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

