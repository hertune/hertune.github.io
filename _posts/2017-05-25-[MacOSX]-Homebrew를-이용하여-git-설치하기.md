---
layout: post
title: "[MacOSX] Homebrew를 이용하여 git 설치하기"
date: 2017-05-25
image: ''
description:
tags:
- MacOSX
- homebrew
categories:
- MacOSX
twitter_text: "[MacOSX] Homebrew를 이용하여 git 설치하기"
---

  Homebrew 설치 완료를 했으니 본격적으로 사용해보자.   

  첫번째 단계는 Homebrew를 통한 git 설치이다. 먼저 터미널을 실행하여 git의 버전을 살펴본다.  

  {% highlight bash %}
  $ git --version
  {% endhighlight %}

  ![img](https://c1.staticflickr.com/5/4221/34885312215_e87642b5fc_b.jpg)    

  맥에는 기본적으로 git이 설치되어 있다. 하지만 Apple에서 기본적으로 설치되어 있는 패키지들은 대부분 과거 버전이 많다. 물론 과거 버전이 무조건 안좋다는 이야긴 아니지만 패키지 관리를 위해 Homebrew를 통해 git을 재설치 하기로 했다.  

  {% highlight bash %}
  $ brew install git
  {% endhighlight %}

  설치 코드는 매우 간단하다. git을 설치한 이후 `brew info git` 명령어를 통해 Dependencies 목록에 (x)표시가 되어 있는 항목들을 다시 설치해주자.  

  사실 이 글을 남기는 이유는 git 설치도 있지만 path가 제대로 잡히지 않을 경우를 대비해서 이다. git path를 확인하기 위해 다시 한번 `git --version`을 입력해준다.  

  만약 이때 버전이 기존 버전과 다르다면 그냥 이용하면 된다. 하지만 기존 버전이 계속 잡힐 수 있다. 개인적으로 `git version 2.11.0(Apple Git-81)`가 동일하게 나왔다.  

  두 가지 방법이 있는데 사실은 동일한 방법이다.  

  1. 터미널에 `echo "export PATH=/usr/local/bin:$PATH" >> ~./bash_profile` 명령어를 입력해준다.  


  2. `vi ~/.bash_profile`을 열고 `export PATH=/usr/local/bin:$PATH`을 입력해준다.  

  이후 `source ~/.bash_profile`을 입력하고 `git --version`을 확인해보면 버전이 바뀌어 있는 것을 볼 수 있다.  
