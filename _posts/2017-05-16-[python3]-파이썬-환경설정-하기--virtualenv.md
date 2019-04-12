---
layout: post
title: "[python3] 파이썬 환경설정 하기 - virtualenv"
date: 2017-05-16
image: ''
description:
tags:
- python3
- python
- virtualenv
categories:
- programming
- python
twitter_text: "[python3] 파이썬 환경설정 하기 - virtualenv"
---

 나는 프로그래머는 아니다.  
 하지만 분석을 위해 가끔 프로그래밍을 하곤한다.  
 미천한 실력이지만 향후 개인설정 및 성장노트(?)겸 기록을 위해 글을 남겨두려 한다.  
 시작은 `python`이다.  

 `R`을 하면서도 느꼈던 점이지만 프로그래밍의 핵심은 소스코드 관리에 있다.  

 프로그래밍을 하면서 주석을 다는 것은 쉬운일이 아니며, 변수명을 설정하고 그에 대한 설명을 적어놓는 것 역시 단순하지만 습관화되지 않는다면 어려운 작업이다. 작업하면서 생산성을 떨어뜨릴 수도 있고 집중력을 흐트러놓을 수도 있다. 하지만 가장 중요한 것은 내가 짠 코드를 나만 알아보는 것이 아닌 `내가 짠 코드를 남도 알아볼 수 있는 것`이 이 시대의 프로그래머들에게 주요한 과제라고 할 수 있다.  

  일부는 동의하지 않을 수도 있다. 하지만 대형 프로젝트에서는 이 모든걸 문서화해서 남겨놓는다. *시스템이나 프로그래밍을 하고 나면 개선사항들이 넘처나기 때문이다. 그것을 한 사람이 다 할수도 없고, 다 한다고 하더라도 그 개선사항을 그 사람이 또 맡기란 쉽지 않은 일이기 때문이다.* ~~업계를 떠날 수도 있고 죽을 수도 있고 사람일은 다양하기 때문에~~~  

  R을 활용할 때에 주석을 쓰려고 노력하는 편이었고 공유는 Github라는 좋은 SVN이 있지만 잘 사용하지 못하는 편이라 `R project`를 만들어서 관리하였다. 하지만 환경이 달라지면 ~~(나와 같은 경우는 맥을 쓰는데 윈도우로 옮겨갈 경우에는 더욱이!!!)~~ 이것도 어느순간 무용지물이 된다.  

  파이썬은 가상환경을 도와주는 라이브러리가 있다. 바로 `virtualenv`이다. 파이썬3가 설치되어 있다는 가정하에 다음 코드를 이용하면 쉽게 설치되어 있다.  

  {% highlight bash %}
  # 물론 파이썬2와 파이썬3이 동시에 설치된 경우엔 pip3를 적어줘야 한다.
    $ pip3 istall virtualenv
  {% endhighlight %}

  virtualenv를 설치한 후 원하는 디렉토리로 이동하여 쉽게 설치할 수 있다.  

  {% highlight bash %}
    $ virtualenv ~/Desktop/Files/test
    $ cd ~/Desktop/Files/test
  {% endhighlight %}

  가상환경을 설치 후 실행할 땐  

  {% highlight bash %}
    $ source bin/activate

    # 이렇게 실행을 하면 터미널 앞에 (test)...$ 이라는 표시가 붙는다.
    # 라이브러리도 다시 다운을 받아준다.
    # 이때 주의할 것은 가상환경에 받아진 라이브러리는 다른 환경에서 실행되지 않는다.
    # 고로 다시 설치해야한다.

    (test)...$ pip3 install beautifulsoup4
    (test)...$ python3
    > from bs4 import BeautifulSoup
    >

    # 환경을 종료할 때는 다음과 같이 입력한다.
    (test)...$ deactivate
  {% endhighlight %}

 이런 식으로 virtualenv를 활용하면 다른 사람과 같이 협업하기도 편리하다.  

  하나 더 추가하자면 라이브러리 설치에 관한 것이다. 가상환경에 설치된 라이브러리는 위에 주석처럼 다른 환경에서 실행되지 않는다. 그래서 가상환경 폴더를 이동시킬 때 추가 설치를 해야하는데 이를 커맨드로 좀 더 간편하게 할 수 있다.  

 {% highlight bash %}
    (test)...$ pip freeze > pkg_list.txt
    (other_test)...$ pip3 install -r pkg_list.txt
 {% endhighlight %}

  다음과 같이 커맨드를 입력하면 첫 줄에서는 가상환경에서 설치된 라이브러리 목록들을 볼 수 있다. 두번째는 다른 폴더로 이동했을 경우 pkg_list에 들어 있는 라이브러리를 설치할 수 있다.  
