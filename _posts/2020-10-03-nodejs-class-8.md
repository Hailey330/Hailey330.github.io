---
layout: 'post'
title: 'JavaScript 객체의 형식과 반복'
description: '8. 자바스크립트에서의 객체와 객체의 반복'
date: 2020-10-03 16:47
categories:
  - Programming
tags:
  - Nodejs
  - JavaScript
---


# 배열과 객체의 차이
### 배열(Array)
들어오는 정보를 순서대로 정리합니다.   
배열에서 각각의 정보(Element)는 식별자가 존재합니다. 

```javascript
var members = ['hongcha', 'hailey', 'hoya'];
console.log(memebers[1]); // console : hailey
```
<br/>

### 객체(Object)
순서가 없는 정보를 저장하기에 최적인 수납상자 개념입니다.   
숫자로 식별자를 두지 않습니다. 

```javascript
var roles = {
    'programmer':'hongcha',
    'designer' : 'hailey',
    'manager' : 'hoya'
}
console.log(roles.designer); // console : hailey
console.log(roles['designer']); // console : hailey
```
<br/><br/>


# 배열과 객체의 반복
배열의 반복은 while문, 객체의 반복은 for문으로 동작합니다. 

```javascript
var members = ['hongcha', 'hailey', 'hoya'];

// 배열의 반복
var i = 0;
while(i < members.length) {
    console.log('array loop', memebers[i]);
    i = i + 1;
}

var roles = {
    'programmer':'hongcha',
    'designer' : 'hailey',
    'manager' : 'hoya'
}

// 객체의 반복
for(var name in roles) { // key = name
    console.log('object => ', name, 'value => ', roles[name]);
}
```
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
