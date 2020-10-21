---
layout: post
title:  "[Java] HashMap 정리"
author: "Misun"
categories: [ TIL ]
comments: true
---
HashMap을 잘 사용하지않았더니 개념이 아리송송해서 다시 한번<br />
정리해보는 시간을 갖기로 위해서<br />
오랜만에 https://docs.oracle.com/javase/8/docs/api/ 에 접속했다<br />

```
getOrDefault
default V getOrDefault(Object key, V defaultValue)
찾는 키가 존재한다면 찾는 키의 값을 반환하고 없다면 기본 값을 반환한다.
```