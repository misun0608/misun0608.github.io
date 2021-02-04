---
layout: post
title: "[Spring]Request method 'GET' not supported 에러"
author: "Misun"
categories: [TIL]
comments: true
---

ajax를 이용해서 데이터를 받아오는데 계속 Request method 'GET' not supported 에러가 났다. 분명히 Controller와 ajax에 모두 method를 post로 지정해놨는데 왜 그런지 모르게 get를 찾을 수 없다는 오류가 계속 났다. 검색을 해봐도 method를 모두 같게 지정해줘야한다고만 나와서 너무 답답했다.<br>
<br>

그러다 예전 프로젝트를 찾아봤는데 Jackson을 설정해놓은 걸 발견했고 아래와 같이 pom.xml 에 추가를 했다.

```xml
<!-- Jackson JSON Mapper 시작 : jackson-core springframework 5.X.X에 사용 -->
<dependency>
<groupId>com.fasterxml.jackson.core</groupId>
<artifactId>jackson-databind</artifactId>
<version>2.9.6</version>
</dependency>
<!-- Jackson JSON Mapper 끝 -->
```

<br>
허무하게도 오류가 해결됐다. 진짜 하루종일 오류때문에 고생한거 같은데 한순간에 해결돼서 홀가분하면서도 내 자신이 한심하게 느껴지는 순간이었다.<br>
