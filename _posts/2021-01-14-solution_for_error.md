---
layout: post
title:  "[Spring]Handler dispatch failed; nested exception is java.lang.AbstractMethodError 에러"
author: "Misun"
categories: [ TIL ]
comments: true
---
확실히 세팅하는게 진짜 힘든거 같다.<br>
기존에 Oracle을 쓰다가 MySQL을 연동해서 쓰려니까 이상한 오류들을 많이 만날 수 있었다.<br><br>

그 중에<br>

```
Handler dispatch failed; nested exception is java.lang.AbstractMethodError: 
org.mybatis.spring.transaction.SpringManagedTransaction.getTimeout()Ljava/lang/Integer;
```

이런 오류를 만나서 또 열심히 해결방법을 찾고 있었는데<br>

<https://do-study.tistory.com/20> 에 보니 버전오류인 거 같았다<br>

```
<groupId>org.mybatis</groupId>
<artifactId>mybatis-spring</artifactId>
<version>1.3.0</version>
```

이 블로그의 조언대로 pom.xml에 mybatis-spring 버전을 1.3.0으로 바꿔주니 해결됐다.<br>
감사합니다... 감사합니다.. <br><br>
개발하면서 느끼지만 정말 한끗차이로 오류가 나는 경우가 참 많다.<br>
그런 작은 차이를 이해하고 개발하기 위해선 얼마나 많은 시행착오를 겪어야 할까?<br>
잘하는 개발자가 되고싶다.<br>