---
layout: post
title: "[IntelliJ]HttpServletRequest 추가"
author: "Misun"
categories: [TIL]
comments: true
---

인텔리제이에서 HttpServletRequest를 사용하기 위해서는 Dependencies에 톰캣 라이브러리를 추가해야 한다.<br>

### 추가 방법

- Project Structure -> Modules -> Dependencies 를 들어간다.

![Image with caption](../img/Tomcat/http01.png "방법")
![Image with caption](../img/Tomcat/http02.png "방법")

- Add(+) 선택 -> Library -> From Maven

![Image with caption](../img/Tomcat/http03.png "방법")
![Image with caption](../img/Tomcat/http04.png "방법")

- Tomcat 사용하는 버전을 선택한다.
  참고로 톰캣이 연결돼어있지 않다면 이 창에서 아무것도 찾을 수 없으니 일단은 IntelliJ와 Tomcat을 꼭 먼저 연동해야한다.<br>
  [연결방법](https://goddaehee.tistory.com/247)

![Image with caption](../img/Tomcat/http05.png "방법")

#### 출처

<https://xzio.tistory.com/1287>
