---
layout: post
title: "[MacOSX] 패키지 관리 tool homebrew 설치하기"
date: 2017-05-23
image: ''
description:
tags:
- MacOSX
- homebrew
categories:
- MacOSX
twitter_text: "[MacOSX] 패키지 관리 툴 homebrew 설치하기"
---

## Homebrew에 대해서

  맥을 사용하는 사람들 일부는 알고 있으리라 생각하지만 설치된 패키지나 어플리케이션에 대한 버전관리가 쉽지않다. 항상 개인적으로 고생했던 것 중 하나는 버전업이 되었을 때 앱스토어를 통해서 업그레이드가 가능한 패키지가 있고, 새로운 버전을 설치해야 하는 패키지가 있다.  

  이를 좀 더 유연하게 관리하기 위해 맥의 패키지 관리툴중 하나인 `MacPort`를 사용했었으나 관리자(Sudo) 권한으로 실행해주는 문제점과 버전관리가 생각보다 쉽지 않고 복잡한 문제들이 있어서 알아보던 찰나 `Homebrew`라는 좋은 관리툴이 있어서 소개하기로 한다.  

## Homebrew 설치하기

  `Homebrew`의 설치조건은 `xcode`가 필요한데 이는 앱스토에서 다운 받거나 혹은 터미널에서 다음과 같은 간단한 명령어를 통해 다운 받을 수 있다.  

  {% highlight bash %}
    $ xcode-select --install
  {% endhighlight %}

  혹시 기존에 `xcode`가 있는데 `homebrew` 설치의 문제가 있다면 업데이트를 해야한다. 있는지 없는지 확인이 필요하다면 다음과 같이 터미널에 입력하여 확인해본다.  

  {% highlight bash %}
  # 경로를 확인한다.
  $ xcode-select -p

  # gcc의 버전을 확인한다.
  $ gcc --version
  {% endhighlight %}

  이제 본격적인 `Homebrew` 설치다. 하지만 막상 별거 없다. 다음과 같이 한줄만 입력하면 끝이다.  

  {% highlight bash %}
  $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/
    install/master/install)"
  {% endhighlight %}

  ruby와 curl을 이용해 설치하는데 만약 설치가 실패한다면 [Homebrew 링크](https://brew.sh/index_ko.html)를 타고 들어가 확인해보자.

## 설치 후 해야할 것

  `.bash_profile`로 들어가 다음과 같이 **export** 시켜준다. 그리고 패키지 설치시 심볼릭 링크를 생성하는 디렉토리에 권한 수정을 해준다.

  {% highlight bash %}
  # .bash_profile 변경
  export PATH=$(brew --prefix ruby)/bin:$PATH

  # 디렉토리 권한 설정
  $ sudo chown -R $USER /usr/local
  {% endhighlight %}

  이후 brew 명령어들을 통해 사용하면 된다. brew 명령어는 2부에 계속 하겠다.
