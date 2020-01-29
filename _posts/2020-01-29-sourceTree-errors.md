---
layout: post
title: "[소스트리] Please make sure you have the correct access rights and the repository exists 에러 해결" 
categories: error
tags: error
---

-   버전 : 소스트리 4.0
-   에러 메시지: Please make sure you have the correct access rights and the repository exists
-   환경: 소스트리 계정 > 계정에서 깃허브 계정이 추가만 되어있는 상태

---

맥북으로 개발 환경을 바꾸고 나서 소스트리를 사용하려고 하는데,

Please make sure you have the correct access rights and the repository exists 에러 메시지와 함께 깃헙 푸시가 되지 않는 에러가 있었다. 찾아보니 맨 처음 깃허브를 사용할 때 필요한 깃허브 계정 초기 설정과 ssh 키 등록을 하지 않아서 발생하는 문제였다.  
  

### 깃허브 계정 설정

먼저 git --version으로 git이 설치되어있는지 확인한다. 만약에 버전이 뜨지 않는다면 [Git for Mac](https://git-scm.com/download/mac) 에서 인스톨러를 다운로드 받아서 진행하자.

깃허브 초기 설정은 다음과 같다.

```
git config —global user.name "깃허브 계정명"
git config —global user.email 깃허브 가입한 이메일

```

설정을 확인하고 싶으면 git config --list로 체크해본다.  
  
  
  

### ssh 키 생성하기

ssh는 키를 만들면 공개키(public Key)와 비공개키(private Key)가 자동적으로 생성되는데, 우리는 rsa 공개키를 사용할 것이다.

윈도우는 조금 더 복잡했던 것으로 기억하지만, 맥북 터미널에서는 간단한 명령어로 키 생성이 가능하다.  
(수행 도중에 물어보는 것은 모두 디폴트 값으로 넘겨도 좋다.)

이 명령어를 수행하고 나면 .pub 파일이 생성되는데, 이 파일을 찾기 위해서는 맥북의 파인더에서 숨김 파일을 보기 위한 간단한 터미널 설정이 필요하다.

```
ssh-keygen

defaults write com.apple.finder AppleShowAllFiles YES
```

이후에는 cat 명령어로 공개키 파일 이름을 통해 찾은 다음 pbcopy로 .pub 파일의 내용을 복사해서 소스트리 깃허브 계정에 붙이거나 깃허브 settings> SSH and GPG keys에서 직접 키를 등록하는 방법이 있다.

```
cat ~/.ssh/id_rsa.pub
pbcopy < ~/.ssh/id_rsa.pub
```

  
  
소스트리 계정> 계정에서 ssh 키: id\_rsa.pub이 확인된다면 푸시도 정상적으로 작동될 것이다.

![]({{ site.url }}/assets/st.png)
