---
layout: 'post'
title: 'Node.js 입력과 출력 정보에 대한 보안'
description: '11. Node.js 입출력 정보의 보안에 대하여'
date: 2020-10-03 20:03
categories:
  - Programming
tags:
  - Nodejs
---


# 입력 정보에 대한 보안
### 보안의 중요성
데이터베이스는 ID 와 PW 가 존재해야 데이터를 가져올 수 있습니다.   
그러기 위해서는 데이터를 어딘가에 저장해야 합니다.   
이 데이터를 가상의 `password.js` 에 저장한다고 하면, password 정보가 사용자의 화면에 그대로 출력되는 문제가 발생할 수 있습니다. 이렇게 되면 서버의 상위 폴더 구조까지 알게 되는 끔찍한 상황이 생길 수 있기 때문에 보안은 웹에서 아주 중요합니다.


사용자가 입력한 정보(외부에서 들어온 데이터)와 이 정보가 밖으로 나갈 때 모두 오염될 가능성이 있어서 모든 것을 철저하게 의심해봐야 합니다. 


### 방법

![image](https://user-images.githubusercontent.com/57790541/94997764-2ec2c500-05e8-11eb-87d3-e35a411673b4.png)
* `main.js`의 id 값을 숨겨서 전송하기 위해 `path.parse()` 를 사용합니다. 


![image](https://user-images.githubusercontent.com/57790541/94997853-dcce6f00-05e8-11eb-80a1-4d1a1ef58321.png)
* 쿼리 스트링에 파일명을 쳐도 내용은 보이지 않게 됩니다. 


# 출력 정보에 대한 보안
### XSS 공격
웹에서 텍스트로 `<script>alert('merong');</script>`와 같은 스크립트 코드를 작성할 경우, 그대로 실행되는 경우가 발생합니다. 이런 경우가 커져 사용자의 로그인 정보를 갈취한다던지 서버의 정보를 해킹하는 등 심각한 문제가 생길 수도 있습니다.   

### 방법 
1. script 태그 필터링하기 
2. 태그의 꺽쇠를 웹 브라우저에 그대로 표시하기 
```javascript
&lt;script&gt;
~
&lt;/script&gt;
```
3. npm 을 통해 만들어둔 모듈을 사용하기
스크립트 비활성화 하는 'sanitize html' 모듈이 있습니다.   
먼저, 설치하기 전에 모듈의 평판을 살펴보고 사용하는 것이 좋습니다.   
```
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (nodejs) 
version: (1.0.0) 
description: 
entry point: (main.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
About to write to /Users/minkyung/Documents/nodejs/package.json:

{
  "name": "nodejs",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "directories": {
    "lib": "lib"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

Is this OK? (yes)
```
* 설치하고나면 `package.json` 이라는 패키지가 생성됩니다. 


```
$ npm install -S sanitize-html
```
![image](https://user-images.githubusercontent.com/57790541/94998066-48fda280-05ea-11eb-8133-bd5103873f9b.png)
* dependencies 에 'sanitize-html' 이 추가된 것을 확인할 수 있습니다. 


![image](https://user-images.githubusercontent.com/57790541/94998091-5fa3f980-05ea-11eb-9517-712b89131f00.png)
* 코드를 수정해줍니다. 


![image](https://user-images.githubusercontent.com/57790541/94998101-6cc0e880-05ea-11eb-9ebe-f778ed8b3474.png)

![image](https://user-images.githubusercontent.com/57790541/94998121-7f3b2200-05ea-11eb-901c-d69ddaa5cf94.png)
* 생성된 파일 안에 스크립트 태그가 존재하지만, 알아서 없는 것처럼 보여줍니다.


```javascript
var sanitiezedDescription = sanitizeHtml(description, {
  allowedTags:['h1']
  });
```
![image](https://user-images.githubusercontent.com/57790541/94998153-a98cdf80-05ea-11eb-99ba-f845103f943c.png)
* 일부 태그를 허용할 수도 있습니다. 
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
