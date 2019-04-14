---
layout: post
title: "[가상화폐] 이더리움 지갑 만들기_myEtherWallet"
date: 2017-06-06
image: ''
description:
tags:
- 가상화폐
- 가상화폐 지갑
- 마이이더웰렛
- 메타마스크
- 비트코인
- 알트코인
- bitcoin
- ethereum
- altcoin
- myEtherWallet
- metamask
categories:
- 가상화폐
twitter_text: "[가상화폐] 이더리움 지갑 만들기_myEtherWallet"
---

  [이전 포스팅](http://joshualog.com/%EA%B0%80%EC%83%81%ED%99%94%ED%8F%90-%EB%B9%84%ED%8A%B8%EC%BD%94%EC%9D%B8%EA%B3%BC-%EC%A7%80%EA%B0%91%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B3%A0%EC%B0%B0/)을 살펴보면 가상화폐 거래소의 해킹의 위험성에 대해 설명을 하고 지갑의 종류에 대해 알아보았다. 가상화폐 거래소의 종류에 대해 포스팅을 하려고 했으나 그보다 먼저 내가 자주쓰는 지갑에 대해 소개하려고 한다.  

  가상화폐라고 하면 대부분 잘 이해가 안갈지도 모르겠으나 '**비트코인**'이라고 이야기하면 한번쯤 들어보셨으리라 생각한다. 그러나 오늘 만들 지갑은 비트코인이 아니다. 개인적으로 비트코인을 사용하고는 있으나 다른 용도로 투자하였기 때문에 아직 거래소로부터 안전한 장소에 보관하고 있지 않다. 하지만 '**이더리움**'은 따로 지갑을 갖고 사용하고 있다.  

  가장 많이 사용하는 '**이더리움**'지갑 중에 웹지갑 형태로는 2가지가 있다.  

  - [MyEtherWallet](https://www.myetherwallet.com/)
  - [MetaMask](https://metamask.io/)

  둘다 크롬에서 확장형 App을 가지고 있고 dApp(Decentralized Application)에서 실제로 이더로 거래도 가능하다. 오늘은 그 첫번째 시간으로 [MyEtherWallet](https://www.myetherwallet.com/)에 대해 알아보자.

## Installing and setting MyEtherWallet

### 1. Generating Wallet Address

  [MyEtherWallet 홈페이지](https://www.myetherwallet.com/)로 이동하면 다음과 같은 화면을 볼 수 있다.

  ![Generating MyEtherWallet](https://c1.staticflickr.com/5/4250/34276738424_77bc1d6b03_b.jpg)

  지갑을 생성하기 전에 가장 먼저 해야할 것은 주소를 만들어 주는 것이다. 비밀번호(최소 9자리 이상)을 입력하고 Generate Wallet 버튼을 클릭한다.

  ![KeystoreFileMEW](https://c1.staticflickr.com/5/4217/34956703042_8496612495_b.jpg)

  그럼 위와 같은 페이지가 생성된다. 해당 '**Keystore File**' 안전한 위치에 다운 받는다. 향후에 한꺼번에 지갑의 기능에 대해 설명할 것이다.  


  하지만 잠깐 이야기하자면,

  > Keystore File은 백업이 되기 전까지 **지우거나 잊어버려서는 안된다.** (저장 위치를 잘 기억하고 있자)

  현재는 지갑 주소를 생성하면 '**Keystore File**'이 생성된다는 것을 알고 있기만 하면 된다.

### 2. download chrome extension app : MyEtherWallet CX

  Chrome Browser가 설치되어 있다면 Chrome Web Store에서 'myetherwallet cx'를 검색한다.  

  ![ChromeWebStroe myEtherWallet](https://c1.staticflickr.com/5/4224/34990648991_d114924c8f_b.jpg)

  그럼 다음과 같은 두가지 App이 검색이 될 것이다. ~~현재 필자의 컴퓨터에는 MyEtherWallet CX가 확장 프로그램으로 깔려 있어서 설치됨으로 표시된다.~~ 맨 처음 검색되는 MyEtherWallet CX와 같은 경우는 우리가 사용할 ethereum 지갑이다. 두번째 ClassicEtherWallet CX는 ethereum class 지갑이다. etehereum은 hard fork로 인해 2가지 종류의 코인이있고 이름은 비슷하나 다른 코인이라고 생각하면 쉽다.  

  ![ChromeApp myEtherWallet](https://c1.staticflickr.com/5/4272/34957057212_5f7abaa95e_b.jpg)

  다운로드가 완료되면 상단에 <i class="fa fa-refresh" aria-hidden="true"></i>
  와 같은 아이콘이 생성된다. 이 아이콘을 누르면 다음과 같은 화면이 나타난다. 바로 이 앱이 'MyEtherWallet CX'이다.

  ![myEtherWallet add](https://c1.staticflickr.com/5/4272/35121869255_c5b6d68199_b.jpg)

  ~~이미 개인적으로 2개의 주소를 갖고 있기 때문에 해당 주소와 잔액이 화면에 표시된다. 처음 앱을 만든 사람은 아직 주소와 잔액이 표시되지 않을 것이다.~~  


### 3. Adding your ether Wallet

  ![Adding myEtherWalletCX1](https://c1.staticflickr.com/5/4222/34277451894_e3eda5a67b_b.jpg)

  지갑 추가 버튼을 누르면 새로운 브라우저에서 myEtherWallet CX 사이트로 이동한다. 지갑추가 목록이 나오는데 이 중 처음 Generate Wallet 버튼을 클릭하여 받아두었던 Keystore File을 선택하고 파일을 불러온다.  

  ![Adding myEtherWalletCX2](https://c1.staticflickr.com/5/4286/35082394256_0843160938_b.jpg)

  암호를 입력하고 잠금해제 버튼을 클릭하면 자신의 계정주소가 나타나고 닉네임을 정할 수 있다. 예제에서는 'joshualogWallet' 이라고 이름을 정했지만 자신이 알아보기 편한 이름을 입력하고 지갑추가 버튼을 누르면 된다.

  ![Adding myEtherWalletCX3](https://c1.staticflickr.com/5/4240/35122141735_15c1066fa8.jpg)  

  다시 MyEtherWallet CX <i class="fa fa-refresh" aria-hidden="true"></i> 아이콘을 클릭해보면 자신의 지갑이름과 주소, 잔액이 표시된다.  

### 4. Back up your ether Wallet

 향후 지갑을 사용하다보면 많은 기능이 있는 것을 알게 될 것이다. 개인적으로 공부를 하고 그 기능들을 소개하려고 한다. 그러나 가장 중요한 것은 **언제, 어디서든 자신만이 접근할 수 있도록 지갑을 백업해 두는 것** 이다. 실제로 트레이딩을 하거나 ICO를 하시는 분들은 몇 천단위 혹은 억단위의 결제를 지갑을 통해 하곤 한다.  

 자신의 자산이 걸려있는 만큼 지갑의 백업은 무엇보다 중요하다. 지금부터 지갑을 백업하는 방법에 대해 설명할 것이다. <i class="fa fa-refresh" aria-hidden="true"></i>에서 내 지갑이라고 써 있는 버튼을 누른다.  

 ![Backup MyEtherWalletCX1](https://c1.staticflickr.com/5/4239/34957739682_6b6a8f3488_b.jpg)

 해당 버튼을 누르면 MyEtherWalletCX 사이트에 접속되어 자신의 지갑 목록이 뜰 것이다. 방금 추가했던 *joshualogWallet* 을 백업해보자.

 가장 우측을 보면 <i class="fa fa-pencil" aria-hidden="true"></i>, <i class="fa fa-eye" aria-hidden="true"></i>, <i class="fa fa-times-circle" aria-hidden="true"></i> 와 같은 세가지 아이콘이 뜬다. 기능을 살펴보면 다음과 같다.

  - <i class="fa fa-pencil" aria-hidden="true"></i> : 지갑 이름변경
  - <i class="fa fa-eye" aria-hidden="true"></i> : 지갑 정보보기
  - <i class="fa fa-times-circle" aria-hidden="true"></i> : 해당 지갑삭제

  우리가 해야할 것은 지갑정보를 백업하는 것으로 <i class="fa fa-eye" aria-hidden="true"></i> 버튼을 클릭하고 비밀번호를 입력한다.  

  ![Backup myEtherWAlletCX2](https://c1.staticflickr.com/5/4232/34278091864_a2e01c6563_b.jpg)

  향후 이용할 *MetaMask* 나 다른 Device나 지갑에서 자신의 주소를 추가하려면 필요한 정보들이 나타난다.

  좌측의 메뉴부터 설명하자면,

  - 계정주소 : 자신의 계정 주소
  - 계정잔액 : 지갑에 들어 있는 ethereum 잔액
  - 토큰잔액 : ICO나 거래소를 구입하여 얻은 이더 기반 Token 잔액
  - 트랜젝션 내역 : 해당 계정에서 타 계정으로 전송 시 내역
  - 동일한 가치 : 다른 코인으로 환산했을 때 가격

  그리고 우측엔 백업이 필요한 정보들이다. **가장 좋은 방법은 Keystore File을 저장하고, 해당 개인 키의 <i class="fa fa-eye" aria-hidden="true"></i>를 클릭하여 종이 지갑을 인쇄해 놓는 것이다.**  

  다른 지갑이나 다른 디바이스에서 백업은 대부분 개인 키라고 불리는 Private Key와 Keystore File로 가능하다. 반드시 백업하는 습관을 가지도록 하자.  
