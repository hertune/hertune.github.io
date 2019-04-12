---
layout: post
title: "[Dev] VScode extensions 소개_Settings Sync"
date: 2018-01-23
image: ''
description:
tags:
- VScode
- Visual Studio Code
- VScode extensions
- Settings sync
- code editor
- development

categories:
- Dev
twitter_text: "[Dev] VScode extensions 소개_Settings Sync"
---

> 쓸데없이 사용하는 OS가 많아지다 보니 코드에디터를 정할 때에도 한계가 온다. 기존에는 `atom`을 사용했는데 이번에 `VScode`로 이동하면서 세팅 설정을 한꺼번에 맞추기 위해 `Settings Sync`라는 extension을 사용하였다.

# Introduction of Settings Sync

 VScode의 extensions 중 하나인 [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)는 Gist를 이용하여 VScode의 세팅 값이나 extensions들을 OS마다 동일하게 맞춰줄 수 있다.

## 1) Install

 `ctrl`+`shift`+`X` 를 눌러 검색창에 [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)를 찾는다.

---

## 2) Get gist token

 `Settings` > `Developer settings` > `Personal access tokens`

 [github](http://github.com)에 접속해서 token을 얻는다.

 Token descripton과 gist 항목을 체크한 후 generate token을 클릭하면 token이 생성된다.

 ![github_token1](https://farm5.staticflickr.com/4615/28079222399_1210f577fc_b.jpg)

 한번 토큰이 생성되고 나면 토큰값을 다시 찾기 어렵고, 다른기기에서 설정할 때 아용되니 해당 토큰을 복사한 후 자신이 필요한 곳에 저장해 두는 습관을 가지도록 하자.

 ![github_token2](https://farm5.staticflickr.com/4667/28079222129_de6af35123_b.jpg)

## 3) Upload VScode Settings

 VScode 에서 `shift`+`alt`+`U`를 누르고 해당 토큰을 입력하면 현재 세팅값이 저장된다.

 ![Setting_Sync](https://farm5.staticflickr.com/4768/28079221969_efc6600e32_b.jpg)

 성공적으로 완료되었다면 에러없이 출력창에 다음과 같은 화면이 뜬다. VSCode를 깐지 얼마 안돼 아직 설정은 많이 하지 않았다.

 ```bash
    CODE SETTINGS SYNC UPLOAD SUMMARY
    Version: 2.8.7
    --------------------
    GitHub Token: *********************************
    GitHub Gist: *******************************
    GitHub Gist Type: Secret

    Restarting Visual Studio Code may be required to apply color and file icon theme.
    --------------------
    Files Uploaded:

    Extensions Added:
    code-settings-sync v2.8.7
    vscode-markdownlint v0.12.1
    --------------------
    Done.
 ```

## 4) Download VScode Settings on other OS

 다른 OS나 환경에서 VScode를 실행하고 [Setting Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)를 다운받아 `shift`+`alt`+`D`를 누르면 설정된 값들을 다운로드 한다.

## 5) How to reset Setting Sync

 [github](http://www.github.com)에서 기존 토큰값을 잃어버리거나 연결이 끊기면 재설정을 해서 업로드를 해줘야 한다. 하지만 이부분은 튜토리얼에 따로 나와있지 않으므로 소개하도록 한다.

 `shift`+`ctrl`+`P`를 눌러 Sync를 검색하면 Sync : Reset Extension Settings라고 나온다. 이것을 선택하면 다음과 같은 창이 뜬다.

 ![Setting_Sync](https://farm5.staticflickr.com/4768/28079221969_efc6600e32_b.jpg)

 해당 창이 뜨면, 새로운 token을 입력하여 3)에서 소개한 방식대로 다시 업로드를 하면된다.
