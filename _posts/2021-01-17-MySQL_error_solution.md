---
layout: post
title:  "[MySQL]Every derived table must have its own alias 해결"
author: "Misun"
categories: [ TIL ]
comments: true
---
Cause: java.sql.SQLSyntaxErrorException: Every derived table must have its own alias<br>
이런 오류를 만났다. 어김없이 Oracle과 MySQL의 차이에서 발생한 오류였는데,<br>
MySQL은 서브쿼리에 alias(별칭)을 다 붙여주지 않으면 오류가 난다고 한다.<br>
<br>

```sql
-- 오류발생 SQL
select *
from (select @rownum:=@rownum+1 as rnum, notice_num, notice_title, notice_content,
notice_reg_date, notice_stored_photo1, notice_type
from (select * from trytri.tt_notice order by notice_num desc ) )
where rnum >= #{startRow} and rnum <![CDATA[ <= ]]> #{endRow} and (@rownum:=0)=0

-- 수정 ver.
select *
from (select @rownum:=@rownum+1 as rnum, notice_num, notice_title, notice_content,
notice_reg_date, notice_stored_photo1, notice_type
from (select * from trytri.tt_notice order by notice_num desc) a) b
where rnum >= #{startRow} and rnum <![CDATA[ <= ]]> #{endRow} and (@rownum:=0)=0
```

서브쿼리에 각각 a와 b라는 별칭을 붙여주니 오류가 해결됐다.<br>