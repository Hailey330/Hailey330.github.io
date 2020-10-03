---
layout: 'post'
title: 'JavaScript 객체와 함수'
description: '9. 객체 함수화, 데이터와 처리 방법이 담긴 객체'
date: 2020-10-03 18:27
categories:
  - Programming
tags:
  - Nodejs
  - JavaScript
---


# 함수(function)
프로그래밍을 한다는 것은 크게 2가지로 말할 수 있습니다.   
1. 데이터 
2. 데이터 처리 


데이터를 정리 정돈하는 것에는 객체와 배열이 있는데, 자바스크립트에서 처리하는 것들이 많아지면 함수를 따로 만들어 사용했습니다.   
함수는 처리해야 할 일에 대한 정보를 담고 있는 구문(statement)이면서도 동시에 값(value)이기도 합니다.   
이런 특성을 이용하면 서로 연관된 데이터(변수)와 처리(함수)를 그룹핑해서 정리 정돈할 수 있습니다.


```javascript
// 함수가 다른 statement 와 다르게 값이 될 수 있습니다. 
var f = function () { 
    console.log(1+1);
}

f(); 

// 배열의 원소로써 함수가 존재할 수 있습니다.  
var a = [f];
a[0]();

// 객체로써 함수가 존재할 수 있습니다. 
var o = {
    func:f
}
o.func();
```
* 함수를 배열에 담는 경우보다 객체로써 많이 사용하는데, 이유는 객체는 이름이 존재하기 때문에 담아놓은 함수를 이름으로 꺼내어 쓸 수 있기 때문입니다. 


* 대신, 자바스크립트에서는 조건문이 값이 될 수는 없습니다. 

```javascript
var i = if(true){console.log(1)}; // (X)
var w = while(true){console.log(1)}; // (X)
```
<br/><br/>


# 객체 그룹핑하기
많은 사람들과 협업을 하다보면 각각의 코드 사이에 10만 개의 코드가 작성될 수 있는 상황이 올 수도 있습니다. 위에서 이미 선언한 것을 다시 밑에서 재선언하게 되면, 코드가 꼬이고 버그가 어디에서 발생하는지 찾지 못할 수도 있습니다. 


```javascript
var v1 = 'v1';

v1 = 'hongcha'; // 버그 가능성!
var v2 = 'v2';
```

* 이럴 때를 위해 객체에 담아서 관리하면 쉽고 보기에도 편합니다.   
폴더의 기능과 같다고 생각하면 됩니다.   


```javascript
var o = {
    v1:'v1',
    v2:'v2'
}
```


```javascript
var o = {
    v1:'v1',
    v2:'v2',
    f1:function () {
        console.log(o.v1);
    }
}

function f2() {
    console.log(o.v2);
}

o.f1();
f2();
```


`f2()`를 객체 그룹핑으로 엮어봅시다. 


```javascript
var o = {
    v1:'v1',
    v2:'v2',
    f1:function () {
        console.log(this.v1);
    }, 
    f2:function () {
        console.log(this.v2);
    }
}

o.f1();
o.f2();
```
* 위와 같은 객체 그룹핑으로 코드의 복잡성을 획기적으로 낮출 수 있게 되었습니다.   

> 객체는 서로 연관된 데이터와 데이터를 처리하는 방법인 함수를 그룹핑해서 코드의 복잡성을 낮출 수 있는 수납상자 개념!
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
