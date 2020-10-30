---
layout: post
title:  "[Spring]Maven vs Gradle"
author: "Misun"
categories: [ TIL ]
comments: true
---
나의 첫 프로젝트는 Spring기반이었기 때문에 빌드도구는 Maven을 처음 접했다. 그러다가 최근에 Spring Boot를 공부하기 시작했는데 Gradle을 이용하는 것을 보고 이 둘의 차이점이 뭔지 궁금해졌다.<br /><br />

### 빌드도구란?
Maven과 Gradle을 알아보기 전에 이 둘을 지칭하는 빌드도구에 대해 알아보자.<br >
빌드도구란 빠른 기간 늘어나는 라이브러리을 자동으로 추가하고 버전을 쉽게 관리해주는 도구이다.<br /><br />

### Maven이란?
2004년에 Ant의 불편함을 해소하고 추가기능을 붙여 출시했다.<br
 />
사용할 라이브러리 뿐만 아니라 해당 라이브러리가 작동하는데 필요한 다른 라이브러리들까지 관리하여 네트워크를 통해 자동으로 다운 받아준다.<br /> 
pom.xml을 이용한 정형화된 빌드 시스템을 제공한다.

### Gradle이란?
2012년에 Ant와 Maven의 장점을 모아 출시했다.<br />
안드로이드 앱을 만들때 필요한 공식 빌드시스템이기도 하며 JAVA, C/C++, Python 등을 지원한다.<br />
Gradle은 별도의 빌드스크립트를 통하여 사용할 어플리케이션 버전, 라이브러리등의 항목을 설정 할 수 있다.<br />
Gradle이 Maven에 비해 최대 100배 빠르다고 한다.


### 출처
<https://bkim.tistory.com/13> <br />
<https://hyojun123.github.io/2019/04/18/gradleAndMaven/>