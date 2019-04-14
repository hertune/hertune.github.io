---
layout: post
title: "[Nas] Synology install gogs"
date: 2019-03-23
image: ''
description:
tags:
- nas
- synology

categories:
- Nas
twitter_text: "[Nas] Synology install gogs"
---

> Synology에서 git server를 통해 git을 관리할 수 있으나 [github](https://www.github.com) 이나 [gitlab](https://www.gitlab.com) 처럼 웹 ui가 지원되는 git은 아니다. Synology 자체에 gitlab을 제공하고 있으나 이전에 설치해본 결과 과부하가 너무 심해 조금 찾아보니 gogs, gitea 라는 웹 ui 기반의 설치형 git이 있었다. 

# 1. 설치 전 준비

시놀리지 패키지센터에서 다음 패키지를 설치한다.
- Git Server
- MariaDB 10
- phpMyAdmin

## 1-1. phpMyAdmin을 이용하여 gogs DB 설정


## 1-1. 크롬 버전 확인하기

크롬 버전은 자신의 프로파일 옆의 설정부분에서 `Help` -> `About Google Chrome` 탭에서 확인할 수 있다.

## 1-2. 웹드라이버 다운받기

[웹드라이버 공식 홈페이지](https://sites.google.com/a/chromium.org/chromedriver/downloads)를 확인하고 자신의 맞는 버전을 다운 받은 후 압축을 해제해준다.

# 2. 웹 드라이버 설정하기

먼저 웹드라이버에 접근 권한을 주고, 해당 파일을 이동 시킨 후 링크를 만들어준다

```bash
# 접근 권한
chmod +x chromedriver

# 파일 이동 후 링크 생성
sudo mv -f ~/Download/chromedriver /usr/local/share/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/local/bin/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/bin/chromedriver # Operation not permitted
```




