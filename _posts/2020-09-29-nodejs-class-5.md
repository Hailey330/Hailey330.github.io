---
layout: 'post'
title: 'Node.js 패키지 매니저와 PM2'
description: '5. 패키지 매니저 PM2 사용해보기'
date: 2020-09-30 17:46
categories:
  - Programming
tags:
  - Nodejs
---


# 패키지 매니저 (Package Manager)
패키지 매니저는 소프트웨어들의 업데이트 관리 및 삭제를 도와줍니다. 
* Ubuntu 에서 apt(Advanced Package Tool)가 대표적인 운영체제 패키지 매니저입니다. 
* Python, PHP, Node.js 등 각각의 언어들은 자신만의 패키지 매니저와 소프트웨어 레파지토리를 가지고 있습니다. 


Language | Package manager
Python | pip 
PHP | Composer
Node.js | NPM, Yarn
Java | Maven, Gradle
Ruby | RubyGems, Bundler

<br/><br/>

# PM2 (Process Manager) 
실행 중인 프로그램이 꺼지면 다시 켜주는 역할도 하고 변경된 내용을 자동으로 반영해주는 역할도 하는 노드 프로세스 매니저입니다.   
노드 프로젝트답게 npm 을 통해 pm2 를 설치할 수 있습니다.   

```
$ sudo npm install pm2 -g
```


앞에서 만들었던 프로그램을 pm2 로 실행해봅시다. 

```
$ pm2 start main.js
```
```
$ pm2 start main.js --watch
```
* watch 옵션을 주면 변동사항이 있을 때 재시작합니다. 

![image](https://user-images.githubusercontent.com/57790541/94789544-01232380-0410-11eb-9ea7-d136467d0f10.png)


```
$ pm2 monit
```

pm2 monit 를 이용하면 전체 프로세스에서 발생하는 로그를 터미널을 통해 실시간으로 볼 수 있습니다.   


```
$ pm2 stop main
```

pm2 프로세스 중지하기


```
$ pm2 log
```

pm2 로그 내용 출력하기
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
