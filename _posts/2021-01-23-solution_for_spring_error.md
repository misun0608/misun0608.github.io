---
layout: post
title: "[Spring]HttpMessageNotWritableException: No converter found for return value of type 에러"
author: "Misun"
categories: [TIL]
comments: true
---

개발자가 하는 일은 에러를 개발하는 일이 아닌가 싶다. 그만 만나고 싶다. 에러...<br>

```java
WARN : org.springframework.web.servlet.mvc.support.DefaultHandlerExceptionResolver
 - Failed to write HTTP message:
 org.springframework.http.converter.
 HttpMessageNotWritableException:
 No converter found for return value of type: class java.util.ArrayList
```

이번엔 게시판에 댓글 기능을 추가하면서 Ajax를 사용하는데 오류가 발생했다.<br>
대충 읽어보니 ArrayList 타입을 반환할 수 있는 converter가 없다는거 같은데...<br>
이전에 똑같은 환경에서 했을 때는 잘 돌아갔는데 왜 그런지 잘 모르겠다.<br>
<br>
일단은 이것저것 검색을 해보고 있는데 문제 해결이 된다면 글을 업데이트 하도록 해야겠다.
