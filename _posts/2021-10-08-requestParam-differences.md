---
layout: post
title: "[Spring]@ModelAttribute @RequestParam @RequestBody 차이"
author: "Misun"
categories: [TIL]
comments: true
---

<h3>@ModelAttribute</h3>
<hr>
- 클라이언트가 전송하는 HTTP parameter(URL 끝에 추가하는 파라미터), HTTP Body 내용을 Setter 함수를 통해 1:1로 객체에 데이터를 바인딩한다. <b>Setter 필수!</b><br>
- 여러 파라미터를 매개변수에 바인딩해줄 수 있다.<br>
<br>
<h3>@RequestParam</h3>
<hr>
- HTTP 요청 parameter를 @RequestParam이 쓰이는 메소드의 변수로 Mapping 해주는 역할이다.<br>
- 1:1로 매칭하여 하나의 값만을 전달해준다.<br>
- 필수 여부 default 설정이 true이기 때문에 반드시 해당 파라미터가 요청에 포함되어야 한다.<br>
- 반드시 필요한 변수가 아니라면 required 값을 false로 설정하거나, defaultValue 옵션을 사용하여 default로 사용할 값을 지정해야 한다.<br>
<br>
<h3>@RequestBody</h3>
<hr>
- @RequestBody 애노테이션을 붙이면 HttpMessageReader가 request body를 Java Object로 역직렬화한다.<br>
- body에 담은 값을 변환하기 때문에, GET 이 아닌 POST 방식에서만 사용이 가능하다. (GET 방식은 Header에 값을 담아서 보냄)<br>
- body에 담긴 내용을 변환하기 때문에 @ModelAttribute 처럼 <b>Setter 함수가 없어도 된다</b><br>
- <b>Setter 없이 어떻게 매핑을 할까?</b><br>
    - @RequestBody의 바인딩은 Jackson라이브러리의 ObjectMapper가 수행한다.<br>
    - ObjectMapper는 @RequestBody가 **Property로 구현**되어 있거나 **생성 위임한 경우**가 아니면 **기본 생성자**로 생성한다.<br>
    - ObjectMapper는 Setter와 Getter로 필드를 가져온다.<br>
    - Setter를 사용하지 않고 Reflection을 사용하여 필드 값을 넣준다<br>
<br>
출처<br>
<https://elfinlas.github.io/2018/02/18/spring-parameter><br>
<https://parkadd.tistory.com/70><br>
<https://maivve.tistory.com/298><br>
<https://velog.io/@jh8579/RequestParam-RequestBody-ModelAttrubute>
