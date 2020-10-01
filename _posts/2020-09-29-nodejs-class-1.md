---
layout: 'post'
title: 'Node.js 알아가기'
description: '1. Node.js 처음부터 설치까지'
date: 2020-09-29 17:03
updated: 2020-09-29 17:15
categories:
  - Programming
tags:
  - Nodejs
---


# Node.js? 

NodeJs 는 구글 크롬의 **자바스크립트에 기반해 만들어진 플랫폼**으로, 2009년 라이언 달(Ryan Dahl)에 의해 개발되었습니다. 익숙했던 자바스크립트를 이용해서 웹 애플리케이션을 만들고 싶어진 사람들은 NodeJs의 등장에 열광하게 되고, 웹 브라우저에서만 사용할 수 있었던 자바스크립트가 핫한 컴퓨터 언어로 역전하게 됩니다.   


이 핫한 JavaScript를 이용해서 멋진 웹 애플리케이션을 만들어봅시다!


# Node.js 를 사용하는 목적

### 생산성

만약 1억 개의 웹 페이지가 있다고 가정했을 때, 링크 하나를 수정하려면 1억 개의 페이지를 일일이 다 변경해야 합니다.   
하지만, NodeJs 를 이용하면 한 번만에 다 바꾸는 일이 가능해집니다.   
NodeJs 는 자바스크립트 언어로 이루어져, 하나의 파일 안에 Html 코드가 들어있고 그 코드를 변경하면 아무리 많은 웹 페이지가 존재해도 내용을 한 번에 바꿀 수 있습니다.   
사용자가 어떤 페이지를 요청할 때마다 NodeJs 의 기술로 프로그래밍을 생산해내기 때문에 가능합니다.   
따라서 NodeJs 는 생산성이 매우 뛰어나다고 말할 수 있습니다. 


### 사용자의 참여

Html 은 정적인 파일인데 비해 NodeJs 는 동적이라서 사용자와 정보를 주고 받기가 가능합니다.   
컨텐츠에 대한 읽기 뿐만 아니라 쓰기, 수정, 삭제를 웹을 통해서 제공할 수 있으며, 사용자들이 직접 자신의 컨텐츠를 웹을 통해서 올릴 수 있습니다. 즉, NodeJs 를 이용함으로써 웹의 팽창이 실현됩니다.


# Node.js 설치하기
> Web Browser | Html | Web Application   
> Node.js Runtime | Node.js | Node.js Application

Html 이 Web Application 으로 동작하기 위해서는 Web Brower 가 있어야 하는 것처럼, NodeJs 도 Runtime 을 필요로 하고, 자바스크립트를 작성해 Application 으로 동작합니다.    
따라서 지금부터 NodeJs Runtime 을 설치해봅시다. 


1. [nodejs.org](http://nodejs.org/) 이동하기
![image](https://user-images.githubusercontent.com/57790541/94774498-ff019a80-03f8-11eb-8761-c7b18df91b3f.png)


* 왼쪽과 오른쪽(최신 버전) 둘 다 사용하는데 문제없지만 왼쪽 버전이 좀 더 안정화된 버전이므로 다운로드합니다.


2. 다운로드 받은 파일 압축을 풀고 설치 진행하기
![image](https://user-images.githubusercontent.com/57790541/94774672-5869c980-03f9-11eb-8d98-61d4434c9acc.png)


간단하게 설치가 완료되었으니, 이제부터 NodeJs 를 이용해 동적인 웹 페이지를 만들어봅시다.    


# Node.js 로 웹 서버 만들기
NodeJs 는 기본적으로 Web Server 의 기능을 내장하고 있습니다.   
이런 특성을 이용해 콘텐츠를 프로그래밍적으로 생산할 수 있게 됩니다.   
사용자가 접근할 때마다 자바스크립트를 이용해 정보를 읽는 파일을 만들고, 경로에 해당하는 파일을 찾아서 가져옵니다.   

```javascript
var http = require('http');
var fs = require('fs');
var app = http.createServer(function(request,response){
    var url = request.url;
    if(request.url == '/'){
      url = '/index.html';
    }
    if(request.url == '/favicon.ico'){
      return response.writeHead(404);
    }
    response.writeHead(200);
    response.end(fs.readFileSync(__dirname + url));
 
});
app.listen(3000);
```


# 앞으로의 공부 진행 방향 
1. 필요한 자바스크립트 문법 알기
2. Node.js 기능 배우기 
3. Node.js Application 완성하기

***

## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
* [벨로퍼트 Node.js](https://velopert.com/133)
