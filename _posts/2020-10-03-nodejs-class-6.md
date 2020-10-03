---
layout: 'post'
title: 'Node.js post 방식으로 전송된 데이터 받기'
description: '6. form 태그에서 post 방식으로 전송되는 데이터 받기'
date: 2020-10-03 13:32
categories:
  - Programming
tags:
  - Nodejs
---


# HTML의 form 태그 기본
form 태그를 생성하고, 데이터를 담아 보내봅시다. 


```javascript
<form action="http://localhost:3000/process_create">
<p><input type="text" name="title"></p>
<p><input type="submit"></p>
</form>
```
![image](https://user-images.githubusercontent.com/57790541/94995503-a89f8200-05d9-11eb-816c-c32fc5bc2964.png)

* 다음과 같이 쿼리 스트링이 만들어집니다.   
form 태그는 사용자가 입력한 정보를 `action` 속성이 가리키는 서버로, 쿼리 스트링의 형태로 데이터를 전송하는 기능이 있습니다.   
서버에서 데이터를 넣고 수정하거나 삭제하는 일이 있을 때는 데이터를 URL 로 보내서는 절대 안됩니다.   
눈에 보이지 않는 방식으로 보내야 데이터가 지켜지겠죠?   
그렇게 하기 위해서 form 태그에 `method = post` 를 설정해줍니다. 


```javascript
<form action="http://localhost:3000/process_create" method = "post">
<p><input type="text" name="title"></p>
<p><input type="submit"></p>
</form>
```

![image](https://user-images.githubusercontent.com/57790541/94995656-9d992180-05da-11eb-95e3-8e0aff06f46b.png)


* 이렇게 전송하면 아주 큰 데이터도 문제없이 보낼 수 있습니다. 
<br/><br/>


# POST 방식으로 전송된 데이터 받기
post 방식으로 전송되는 데이터를 NodeJs 안으로 가져오기 위해서는
이벤트를 통해서 데이터를 가져오고, 쿼리 스트링의 모듈 parse 함수를 이용해 정보를 객체화합니다.


```javascript
else if(pathname === '/create'){
      fs.readdir('./data', function(error, filelist){
        var title = 'WEB - create';
        var list = templateList(filelist);
        var template = templateHTML(title, list, `
          <form action="http://localhost:3000/create_process" method="post">
            <p><input type="text" name="title" placeholder="title"></p>
            <p>
              <textarea name="description" placeholder="description"></textarea>
            </p>
            <p>
              <input type="submit">
            </p>
          </form>
        `);
        response.writeHead(200);
        response.end(template);
      });
    } else if(pathname === '/create_process'){
      var body = '';
      request.on('data', function(data){
          body = body + data;
      });
      request.on('end', function(){
          var post = qs.parse(body);
          var title = post.title;
          var description = post.description
      });
      response.writeHead(200);
      response.end('success');
    }
```


![image](https://user-images.githubusercontent.com/57790541/94995797-97577500-05db-11eb-9781-f076144e56ae.png)


![image](https://user-images.githubusercontent.com/57790541/94995808-b3f3ad00-05db-11eb-870e-987c94d5b0cb.png)
* 객체화된 데이터를 확인할 수 있습니다. 
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
