---
layout: 'post'
title: 'Node.js 동기와 비동기 그리고 콜백'
description: '4. Node.js 의 특징인 비동기와 콜백에 대하여'
date: 2020-09-30 16:48
categories:
  - Programming
tags:
  - Nodejs
---


# 동기와 비동기 
처리해야 할 일이 여러 개 있다고 가정해봅시다.   

> Synchronous 동기적 방식
먼저 들어온 일을 처리하고 난 뒤에 단계적으로 일을 처리하는 방식입니다.   
앞의 일이 한 시간이든 두 시간이든 처리할 동안은 들어온 일에만 집중해서 처리합니다. 

> Asynchronous 비동기적 방식
어떤 일을 처리하는데 10시간이 걸린다고 하면, 이 일이 끝날 때까지 기다리는 것이 아니라 처리하는 동안에 다른 일을 동시에 처리하는 효율적인 방식입니다.   
효율적이고 좋지만 그만큼 까다로운 코드 작성이 문제겠죠?   


```javascript
var fs = require('fs');

// 동기적 처리 - readFileSync
console.log('A');
var result = fs.readFileSync('syntax/sample.txt', 'utf8');
console.log(result);
console.log('C');

// 비동기적 처리 - readFile
console.log('A');
fs.readFile('syntax/sample.txt', 'utf8', function(err, result){
    console.log(result);
});
console.log('C');
```

![image](https://user-images.githubusercontent.com/57790541/94782710-991c0f80-0406-11eb-9a10-e892da1e3e42.png)

![image](https://user-images.githubusercontent.com/57790541/94782750-a3d6a480-0406-11eb-9886-f91aa0934304.png)

* fs.readFile 이 처리되는 동안 `console.log('C');` 가 먼저 실행되고, 그 뒤로 result 결과인 B 가 출력됩니다. 
* NodeJs 의 성능을 끌어올리기 위해서는 반드시 비동기적 방식으로 작업해야 합니다. 


# 콜백 (Callback)
콜백 함수는 비동기 방식의 함수로 사용되는 것으로, 일을 다른 객체에게 시키고 그 일이 끝나는 것을 기다리는 것이 아니라 그 객체가 나를 다시 부를 때까지 내가 할 일을 하고 있는 것입니다.   
NodeJs 에서 가장 핵심적인 부분이라고 말할 수 있습니다.    

```javascript
var a = function() {
    console.log('A');
}
a();

function slowfunc(callback) {
    callback();
}

slowfunc(a);
```
`var a` 는 익명 함수로 만들어져, a 값 자체가 함수 값입니다.   
`slowfunc()` 에 a 를 넣으면 콜백 함수로 실행되면서 a 가 가리키는 함수를 실행하게 됩니다. 


***

## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
