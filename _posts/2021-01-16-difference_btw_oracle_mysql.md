---
layout: post
title:  "[MySQL]sysdate, ROWNUM 사용"
author: "Misun"
categories: [ TIL ]
comments: true
---
MySQL과 Oracle은 그냥 세팅? 이정도의 차이만 있을 줄 알았는데 사용하다보니 벌써부터 꽤 많은 차이점을 알 수 있었다.<br>

#### 1.sysdate

Oracle의 sysdate는 MySQL에서 지원이 되지 않는다.<br>
대신 now() 를 쓰면 된다.
<br><br>

#### 2.ROWNUM
Oracle의 ROWNUM도 MySQL에서는 지원하지 않는다.<br>
MySQL에서는 세션변수를 이용한 방법을 이용해야 한다.<br>
<br>

##### 1) SET 구문을 사용하여 초기화

```sql
SET @rownum!=0;

SELECT
@rownum:=@rownum+1
FROM 테이블명;
```

##### 2) FROM절에서 초기화
```sql
SELECT
@rownum:=@rownum+1
FROM 테이블명
,(SELECT @rownum:=0) TMP;
```

##### 3) WHERE절에서 초기화
```sql
SELECT
@rownum:=@rownum+1
FROM 테이블명
WHERE (@rownum:=0)=0;
```

<br>
만약에 초기화를 안할경우 조회할때마다 rownum값이 매번 바뀐다고 하니 주의!