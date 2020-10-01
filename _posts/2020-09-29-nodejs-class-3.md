---
layout: 'post'
title: 'Node.js 동적인 웹 페이지 만들기'
description: '3. Node.js 동적인 웹 페이지 만들기'
date: 2020-09-30 16:00
categories:
  - Programming
tags:
  - Nodejs
---


# URL의 이해 
Web Application 을 구현하는 기본 방식은 URL 로, 같은 파일이지만 URL 주소 뒤에 숫자만 달리해서 다른 페이지를 출력합니다.   

![image](https://user-images.githubusercontent.com/57790541/94778143-9d90fa00-03ff-11eb-99df-b7cc779c048d.png)

* 쿼리 스트링의 값을 변경해 웹 서버에게 데이터를 전달할 수 있습니다.   
* 쿼리 스트링은 '?' 로 시작하기로 약속되어 있고, '=' 으로 문자를 구분합니다. 
<br/>


# 동적인 웹 페이지 만들기 
```javascript
var _url = request.url;
var queryData = url.parse(_url, true).query;
var title = queryData.id;

<head>
  <title>WEB1 - ${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="/">WEB</a></h1>
  <ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
  <h2>${title}</h2>
```
웹 페이지의 타이틀은 쿼리 스트링에 따라서 동적으로 변경됩니다. 
<br/>


# Node.js 파일 읽기 기능 

```javascript
var fs = require('fs');
fs.readFile('sample.txt', 'utf8', function(err, data){
  console.log(data);
});
```
<br/>


# Node.js 파일 목록 알아내기
NodeJs 는 특정 디렉토리의 목록을 배열로 만들어서 전달합니다.   
즉, 배열을 반복문으로 처리해 결과를 얻습니다.   
이걸 이용해 글 목록을 출력할 수 있습니다.   

```javascript
fs.readdir('./data', function(error, filelist){
  console.log(filelist);
})
```
```
출력 결과 : ['CSS', 'HTML', 'JavaScript']
```
<br/>


# Not found 구현하기 
존재하지 않는 정보에 대한 요청이 들어왔을 때 Not found 오류 메시지 전송하는 방법을 알아봅니다. 

```javascript
var pathname = url.parse(_url, true).pathname;
  if(pathname === '/') {
    정상적으로 나올 페이지
  } else {
    response.writeHead(404);
    response.end('Not found');
  }
```
<br/>


# Home 메인 페이지 구현하기 
조건문을 활용해 메인 페이지를 구현해봅니다.
```javascript
if(pathname === '/') {
    if(queryData.id === undefined) { // home 일 때
        fs.readFile(`data/${queryData.id}`, 'utf8', function(err, description) {
					실행될 페이지
				} else {
					HTML, CSS, JavaScript 페이지
		}
} else {
	  response.writeHead(404);
    response.end('Not found');
}
```
<br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
