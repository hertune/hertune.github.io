---
layout: post
title: "[Nas] Synology에 MongoDB 설치하기"
date: 2017-11-18
image: ''
description:
tags:
- Synology
- Nas
- MongoDB
- docker
categories:
- Nas
twitter_text: "[Nas] Synology에 MongoDB 설치하기"
---

  요즘 목표가 생겨서 다시 코딩을 시작중이다. 웹서비스를 진행해볼까 생각하고 Node.js와 react.js에 대해 조금 공부했으나 javascript의 벽에 한계를 느끼고 다시 분석을 먼저 시작하기로 했다.

  그래서 3개월간 synology에서 php + mysql을 통해 실시간 데이터를 가져와 테이블을 만들어주는 작은 사이트를 만들었으나 mysql이 RESTful API에 그다지 적합한 DB는 아니라는 생각이 들었다.

  개인적인 생각으로 SQL이 편하긴 하지만 요즘 데이터들은 대부분 JSON 형태가 많아 column & row 형식으로 바꿔주는 코드를 매번 짜야 했으며, read/write에도 delay가 생겨 NoSQL을 찾게 되었다.

  물론 나는 아직까지 NoSQL은 잘 모른다. ~~쿼리가 복잡하고 join이 없다는 정도 수준이다~~

  NoSQL을 지원하는 DB를 고려하던 중 두가지가 눈에 들어왔다. 하나는 `redis`이고 다른 하나는 `MongoDB`이다. 그러나 가장 큰 문제는 synology가 지원하는 NoSQL DB가 없다는 것이다.

  그래서 결국 `docker`까지 손대게 되었다. 누가 보면 엄청 대단한 것들을 하는 것처럼 느껴질 지 모르겠으나 그냥 다 수박겉핥기 수준이다. 내가 필요한 것들을 내가 아는 수준으로 익히는게 목표다.

  서론이 너무 장황해져서 요약하자면

> PHP + mysql이 현 행태에 적합하지 않아 NoSQL을 찾던 중 Synology에서 지원하는 NoSQL이 없어서 우회수단으로 docker를 통해 MongoDB를 구축하였다.

# 1. install docker

  synology에서 docker를 받는 방법은 간단한다. 패키지 센터에서 docker를 찾아 설치하면 된다.

  현재 무슨이유인지 모르겠으나 패키지센터가 접속이 안되므로 캡처는 추후에 업데이트 하겠다.

# 2. install MongoDB image

  MongoDB image를 설치하기 전에 docker에 대해 아는 수준에서 설명을 하자면, docker는 가상의 환경에 이미지 컴포넌트들을 올려 구동시켜주는 오픈소스이다.

  먼가 장황한 설명이 될지 모르겠는데 기본적으로 컴퓨터에는 OS가 설치되고 프로그램들이 그 위에서 돌아간다. 따라서 우리는 Windows나 Mac, Linux 같은 OS를 가지고 있고 프로그램을 다운받아 실행시킨다.

  만약 Windows의 프로그램을 실행시키려면 Windows가 설치된 컴퓨터에서 실행해야 하며, 나머지 OS들도 마찬가지다. 하지만 docker는 그런 프로그램들을 컴포넌트라는 이미지로 묶어서 프로그램만 가상환경에서 실행시키는 것이다.

  여기서 MongoDB 역시 하나의 프로그램이고 모든 OS에서 실행가능하나 Synology는 linux를 사용하고 있음에도 불구하고 자체 수정된 linux라 그런지 MongoDB 설치가 까다롭다.

  물론 3rd party package center를 찾아보면 있다. 하지만 trouble shooting은 어떻게 할 것인가? ~~나는 컴알못이라 기본적인 설치와 세팅에도 애를 먹었는데...~~

  일반적으로 docker의 이미지들은 회사에서 만들어 배포해주는 경우가 있어서 더욱 믿을만 하다.

  docker가 설치되었다면 `registry` > `mongodb` 를 찾아보자. 다양한 이미지들이 나오지만 기본적으로 믿을만 한 것은 latest version이다.

  ![docker_1](https://farm5.staticflickr.com/4576/24612138188_2b12fa2fd7_k.jpg)

  이를 다운받고 난 후 `image` 탭을 가보면 다음과 같이 MongoDB 이미지가 나타날 것이다. ~물론 명령어로 다운 받는 방법도 있으나 나같은 docker 초보자는 GUI 환경이 더 편하다.~

  ![docker_2](https://farm5.staticflickr.com/4552/24612225668_6b5c7b6581_k.jpg)

  이제 **과감히** 실행버튼을 눌러주자.

  ![docker_3](https://farm5.staticflickr.com/4556/24612307838_2986236c89_b.jpg)

  여기서 몇가지 환경설정을 해줘야한다. 컨테이너 이름은 마음에 드는 것으로 변경하고 docker에서 실행될 때 문제가 하나 있었는데 MongoDB는 보통 `mongod` 라는 커맨드를 이용하여 MongoDB server를 구동하고 다시 `mongo`라는 커맨드로 프로그램을 실행시킨다.

  하지만 *복잡다양한 이유*들로 컨테이너가 죽어버린다. 일반적으로 MongoDB server를 실행시킬 때 코드는 다음과 같다.

  {% highlight bash %}
  mongod --dbpath /data/db
  {% endhighlight %}

  docker에서 이미지파일은 우선적으로 server를 실행시키는 코드다. 따라서 고급설정에 들어가 `볼륨`에서 다음과 같이 폴더를 추가해주고 마운트 경로도 바꿔준다.

  ![docker_4](https://farm5.staticflickr.com/4578/24612576858_1415eda532_b.jpg)

  마지막으로 docker는 admin 계정에서만 실행이 된다. 따라서 서버를 실행시킬 때 `mongod --auth`를 통해 authentication을 설정해줘야 한다.

  `환경`에서 다음과 같이 설정해주자.

  ![docker_5](https://farm5.staticflickr.com/4536/37597459755_0e1c6850b6_b.jpg)

  이제 환경설정이 끝났으니 다음으로 넘어가 적용을 시켜주면 자동적으로 docker에 이미지가 올라가 실행된다.

# 3. setting MongoDB

  ![docer_6](https://farm5.staticflickr.com/4521/38452865832_2e3ca1a76b_k.jpg)

  다음과 같이 이미지가 잘 실행되고 있으면 성공한 것이다.

  우리는 설정을 `--auth`로 했기 때문에 MongoDB의 admin에 자신의 계정을 추가시켜줘야 한다.

  **ssh를 통해 자신의 nas에 접속**하여 MongoDB에 접속한 후 계정추가를 해보자.

  {% highlight bash %}
  # 먼저 root 계정으로 MongoDB에 접속
  # docker는 무조껀 root 계정으로 실행되므로 sudo -i 명령어를 통해 root로 설정해 놓으면 명령어를 사용하기 편하다.
  # docker에 해당 container의 id와 name을 알기 위해 docker ps라는 명령어를 입력한 후 실행

  $ sudo docker ps
  $ sudo docker exec -it <containerName> mongo

  {% endhighlight %}

  해당 커맨드를 입력하면 자신의 docker 안의 MongoDB에 접근할 수 있다. 이제 admin 권한 설정을 하고 authentication 실행을 시켜야 한다.

  {% highlight bash %}

  # admin 권한 설정
  > use admin
  > db.createUser({
                    user: "<username>",
                    pwd: "<password>",
                    roles: [ "readWriteAnyDatabase",
                                "dbAdminAnyDatabase",
                                "clusterAdmin"
                                ]})
  > exit

  # docker 재실행
  $ sudo docker restart <cotainerName>

  # authentication 접속
  $ sudo docker exec -it <containerName> mongo -u '<username>' -p -authenticationDatabase admin

  {% endhighlight %}

  auth접속을 하는 이유는 정확히 모르겠다. docker에서 container가 돌 때 server가 자주 죽는 현상이 있어서 auth접속을 했다. 하다보니 가장 큰 난관에 부딪치게 되었는데 보통 로컬에서는 `mongod.conf` 파일을 수정하여 권한설정 및 초기 시작설정을 해줄 수 있는데 docker 안에서 `mongod.conf`에 접속하기 수월하지 않다.

# 4. 글 마무리

  사실 `mongod.conf`을 찾고 수정하고 싶어서 많은 삽질을 했으나 막상 파이썬에서 실행시켜보니 아무 문제가 되지 않았다. 이러한 삽질의 결과로 나는 docker 명령어들 몇줄을 알게 되었다. 나중에 시간이 되면 docker 명령어와 몇가지 사용법, pymongo를 통해 docker에 올려진 MongoDB 접근하는 방법 등을 설명하려고 한다. 좀 더 능숙해지면 MongoDB 다루는 방법에 대해서도 글을 남기도록 하겠다.

  아이디어들은 많지만 해당 아이디어를 실행하려면 데이터를 쌓아 분석하고 진행해야 한다. 이제 서버에 구축도 했으니 기존에 하던 실시간 데이터 축적 프로젝트를 계속 진행해야겠다. 최근 글이 많이 없던 이유는 잘 모르는 것들에 대해 배워나가느라 글을 쓸 시간이 없었다. 혼자 삽질도 많이하고...하면서도 좌절도 많이하고...'이러면서 발전해 나가겠지?' 라는 긍정적인 생각으로 이 글을 마친다.
