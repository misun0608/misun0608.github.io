---
layout: post
title: "[GitHub].gitignore 파일이 적용 안될때"
author: "Misun"
categories: [TIL]
comments: true
---

github에 올릴 때 올리지 말아야 할 파일을 .gitignore 파일에 추가하면 자동으로 add를 하지 않는다.<br>
그런데 가끔 .gitignore 파일을 수정했을 때 적용이 안되는 문제가 있는데 그에 대한 해결법이다.<br>

### 해결법

```
1. 일단 현재 상태에서 무시하고자 하는 파일을 제외하고 commit을 해준다.
(안 해주면 다 날아가므로 주의하자)
2. 루트 폴더(최상위 폴더)에 간 후 git rm -r --cached . ...
3. git add -A.
4. git commit -m "gitignore 다시 적용"
```

#### 출처

<https://www.google.com/search?q=.gitignore+%EC%A0%81%EC%9A%A9+%EC%95%88%EB%90%A0%EB%95%8C&oq=.gitignore+%EC%A0%81%EC%9A%A9+%EC%95%88%EB%90%A0%EB%95%8C&aqs=chrome..69i57j0i30.8689j0j7&sourceid=chrome&ie=UTF-8>
