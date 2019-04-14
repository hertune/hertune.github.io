---
layout: post
title: "[Ubuntu] ubuntu 설치와 세팅을 위한 삽질 여행기 (part2)"
date: 2017-11-24
image: ''
description:
tags:
- ubuntu
- setting
- boot
- GRUB
- atom
- chrome
- themes
- linuxbrew
categories:
- Ubuntu
twitter_text: "[Ubuntu] ubuntu 설치와 세팅을 위한 삽질 여행기 (part2)"
---

  `ubuntu`를 설치하면서 마음먹었던 일 중 가장 첫번째는 맥과 같은 개발 환경을 구축하는 것이었다. 맥에서는 보통 package manager인 `homebrew`를 이용하여 이것저것 설치한다. 그래서 찾아보니 `ubuntu` 역시도 linuxbrew라는 [brew](http:linuxbrew.sh)를 제공하고 있었다.

  이번 part2에서는 현재 구축한 개발환경을 적어 놓기 위해 좀 빠르게 글을 쓴다. 많은 패키지들을 다운 받고 설치하였기 때문에 그 중간 과정들을 전부 설명하기엔 무리가 있으므로, 개별적인 설명들이 필요하다면 이후에 새로운 글을 작성할 예정이다. ~~항상 예정만...~~

  - GRUB booting 순서 바꾸기
  - linuxbrew 설치하기
  - chrome 설치하기
  - atom 설치하기

# 1. GRUB booting 순서 바꾸기

  보통 처음 GRUB의 화면은 `ubuntu`를 실행하게 되어 있으며 일정시간이 지나면 자동적으로 `ubuntu`가 실행된다. 하지만 보통은 `ubuntu`보다 `windows`를 사용할 일이 많기 때문에 이 순서를 `windows`가 먼저 실행되게 하는 것이 좋다.

  보통 GRUB의 setting은 `/etc/default/grub`  경로 안에 있다.

  {% highlight bash %}
  # 1. adjusting 'config file'

    $ sudo nano /etc/default/grub

  # 2. 'GRUB_DEFAULT = 0' changes to 'GRUB_DEFAULT = saved '
  # 3. save 'ctrl + x' and confirm

    $ cat /etc/default/grub

  {% endhighlight %}

  만약 해당 화면에 `GRUB_DEFAULT = saved`라고 뜨면 잘 저장된 것이다.

  {% highlight bash %}
  # 1. update GRUB

    $ sudo update-grub

  # 2. set booting index
  # 개인적으로 windows가 부팅시 5번째였기 때문에 0부터 시작하여 4를 입력

    $ sudo grub-set-default 4

  # 3. confirm

     $ sudo grub-editenv list

  # 4. result in 'saved_entry = 4'

     $ reboot
  {% endhighlight %}

  이후 reboot을 해보면 원하는 OS가 기본 부팅으로 설정되어 있는 것을 확인할 수 있다.

# 2.  linuxbrew 설치하기

  왜 느닷없이 linux를 설치했냐고 물어본다면, 그냥 이것 때문이다. linuxbrew이 설치에 대한 설명은 해당 [홈페이지](http://linuxbrew.sh)에도 잘 나와 있지만, 그래도 글을 읽느라 고생하시는 분들을 위해 짧은 설명을 추가하려고 한다.

  처음 ubuntu를 깔고 curl이 없는 상태에서 실행한다면 curl부터 설치한다.

  {% highlight bash %}
  # curl install

    $ sudo apt-get install curl

  # linux brew install

    $ sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
  {% endhighlight %}

  이후 path를 설정해 줘야 하는데 Debian/Ubuntu 계열은 ~/.profile에, Redhat/Fedora/CentOS 계열은 ~/.bash_profile에 path를 설정해 준다.

  {% highlight bash %}
  # setting brew path

    $ test -d ~/.linuxbrew && PATH="$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH"

    $ test -d /home/linuxbrew/.linuxbrew && PATH="/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH"

  # if your linux is Debian or Ubuntu :

    $ echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.profile

  # if your linux is Redhat, Fedora or CentOS :

    $ test -r ~/.bash_profile && echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.bash_profile

  # test linuxbrew

      $ brew install hello
  {% endhighlight %}

# 3. chrome 설치하기

 chrome은  가장 간단하다.

 {% highlight bash %}
 $ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
 $ sudo apt-get install libxx1 libgconf2-4 libappindicator1 libindicator7
$ sudo dpkg -i google-chrome-stable_current_amd64.deb
 {% endhighlight %}

# 4. atom 설치하기

 atom도 역시 설치는 쉽다. 나중에 필요한 패키지나 이쁜 테마를 설정하는게 복잡해서 그렇지...

 {% highlight bash %}
 $ sudo apt-get-repository ppa:webupd8team/atom
 $ sudo apt-get update
 $ sudo apt-get install atom
 {% endhighlight %}

 하지만 설치 후에 한글이 깨지는 일이 발생할 수 있으니 세팅을 조금 변경해주자. `Edit` > `stylesheet`로 들어가 `font-family` 속성을 추가한다.

 {% highlight bash %}
    *{
       font-family: "NanumBarunGothic";
       font-weight: bold;
    }
 {% endhighlight %}

 해당 글꼴은 다운 받아야 하지만 part3에 ubuntu themes 변경하는 방법에 대해 포스팅을 하면 그때 같이 설명하겠다.
