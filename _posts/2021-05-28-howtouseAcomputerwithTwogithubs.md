---
layout: post
title: "[GitHub]컴퓨터 하나로 두개의 GitHub 계정 이용하기"
author: "Misun"
categories: [TIL]
comments: true
---

포트폴리오때문에 github계정을 하나 더 사용하려고 했는데 따로 설정이 없이는 오류가 났다. 그래서 또 여기저기 검색을 하기 시작했다.<br>
<br>
찾아보니 SSH(Secure Shell Protocol)를 이용해서 사용할 수 있었다.<br>

<hr>
<h3>SSH란?</h3>
네트워크 프로토콜 중 하나로 컴퓨터와 컴퓨터가 인터넷과 같은 Public Network를 통해 서로 통신을 할 때 보안적으로 안전하게 통신을 하기 위해 사용하는 프로토콜<br>
<hr>
<br>

<h3>어떻게 설정하나?</h3>

~/.ssh/ 이동<br>

```
ssh-keygen -t rsa -C "이메일주소" -f "id_rsa_userA"
ssh-keygen -t rsa -C "이메일주소" -f "id_rsa_userB"
```

적용할 디렉토리로 이동<br>

```
$ ssh-add id_rsa_userA
$ ssh-add id_rsa_userB
```

혹시 개인키 등록에서 오류가 날시에는

```
#ssh-agent를 시작
$ eval $(ssh-agent)
```

을 해주고 하면 오류가 해결된다.<br>

github에 가서 ssh키 등록<br>

config 파일 생성
$ vi ~/.ssh/config
a를 누르고 아래 내용 복사 붙여넣기

```
#Personal account-userA
Host github.com-userA
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_userA

#Personal account-userB
Host github.com-userB
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_userB
```

esc 누르고
:w + enter 누르면 입력모드 끝
다시 :e 누르면 종료

사용자 폴더에 있는

.gitconfig 파일 수정
참고<br>
<https://velog.io/@jay/multiplegithubaccounts>
<https://jcon.tistory.com/185>
<https://rutesun.wordpress.com/2015/02/04/git-bash-개인키-등록시-에러/>
<https://bellog.tistory.com/62>
<https://yangeok.github.io/git/2020/03/08/ssh-multiple-account.html>
