---
layout: 'post'
title: 'Node.js 모듈의 형식과 활용'
description: '10. Node.js 의 모듈에 대하여'
date: 2020-10-03 18:50
categories:
  - Programming
tags:
  - Nodejs
---


# 모듈(Module)
앞에서 데이터를 정리 정돈하는 것은 객체와 배열이 있었습니다.   
그렇다면 '객체'를 정리 정돈할 수 있는 큰 틀은 무엇일까요?   
바로 모듈입니다. 모듈이 가장 큰 도구로 활용됩니다.   
이 모듈을 이용하면 파일을 나눠 웹으로 독립시킬 수 있습니다. 


```javascript
var M = {
    v: 'v',
    f: function () {
        console.log(this.v);
    }
}

module.exports = M;
```
* `module.exports` 는 M이 가리키는 객체를 모듈 밖에서 사용할 수 있도록 exports 하겠다는 것으로 볼 수 있습니다.


```javascript
var part = require('./mpart.js');
console.log(part); 
```
![image](https://user-images.githubusercontent.com/57790541/94997008-2f0c9180-05e3-11eb-808e-d395525726ca.png)


* 콘솔 창에서 확인할 수 있듯이, `console.log(part);`의 결과는 `module.exports`에 대입한 객체임을 알 수 있습니다. 

* `M.f();`와 같은 결과가 나오게 하려면, `part.f();`를 입력해야 합니다. 
<br/><br/>


# 모듈의 활용 
`main.js` 를 모듈화해봅시다.   
먼저, lib 폴더를 생성하고 `template.js` 파일을 만들어서 그 안에 만들어둔 template 객체를 넣어줍니다. 


![image](https://user-images.githubusercontent.com/57790541/94997443-2073a980-05e6-11eb-97ab-2f1a70ba164e.png)
* `main.js`에는 `template.js`를 template 이름으로 import 해줍니다. 


```
$ pm2 log
```
* `main.js`를 실행하면 pm2 가 읽고 있는 모듈의 파일까지 감시합니다.   
모듈 `template.js`의 내용을 수정하면 프로세스를 껐다 다시 켜서 수정된 내용을 반영해줍니다. 
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
