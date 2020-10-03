---
layout: 'post'
title: 'Node.js 파일 생성과 리다이렉션'
description: '7. 파일을 생성하고 해당 파일로 이동하는 것까지'
date: 2020-10-03 14:24
categories:
  - Programming
tags:
  - Nodejs
---


# 파일 생성하기
create 시, data 디렉토리 안에 파일 형태로 데이터를 저장해봅시다.   
이전의 데이터를 title, description 을 나눠서 받을 때 파일로 저장하는 법입니다. 


```javascript
fs.writeFile(`data/${title}`, description, 'utf8', function(err) {
  response.writeHead(200);
  response.end("success");
  })
```


![image](https://user-images.githubusercontent.com/57790541/94995993-e2be5300-05dc-11eb-8c05-d0ea9936a3bd.png)


![image](https://user-images.githubusercontent.com/57790541/94996001-ed78e800-05dc-11eb-96d2-9f8afbc754ed.png)
* 제출 버튼을 누르면, 파일로 저장되는 데이터를 확인할 수 있습니다. 
<br/><br/>


# 리다이렉션하기
사용자가 글을 쓰고, 쓴 글을 바로 확인할 수 있도록 페이지를 리다이렉션하게 만들어 봅시다.   


```javascript
else if(pathname === '/create_process'){
      var body = '';
      request.on('data', function(data){
          body = body + data;
      });
      request.on('end', function(){
          var post = qs.parse(body);
          var title = post.title;
          var description = post.description;
          fs.writeFile(`data/${title}`, description, 'utf8', function(err){
            response.writeHead(302, {Location: `/?id=${title}`});
            response.end();
          })
      });
```
* title 값을 `Location` 의 id 에 넣어주면, 글쓰자마자 해당 글로 이동합니다. 
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
