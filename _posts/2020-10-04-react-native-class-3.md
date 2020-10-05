---
layout: 'post'
title: 'React 기본 - Props'
description: '3. React 기본 Props 에 대하여'
date: 2020-10-04 13:10
categories:
  - ReactNative
tags:
  - ReactNative
---

# Props? 
React 는 다수의 컴포넌트로 이루어져 있는 결정체로, 컴포넌트 간의 값을 공유하기 위해서 Props 객체를 통해 값을 공유합니다. 
* JSP 에서 POST 나 GET 처럼 파라미터를 넘기는 방식

```javascript
<View style = {styles.container}>
  <Text style = {styles.hello}>Hello World!</Text>
  <Image source = {require('./assets/cake.jpeg')} style={{width : 300, height : 300}} />
</View>
```

![image](https://user-images.githubusercontent.com/57790541/95009419-eee9f500-065c-11eb-8232-9ac72bb53f9a.png)

* 컴포넌트를 따로 만들어봅시다. 

```javascript
class Photo extends Component {
  render () {
    return (
      <View>
        <Image source = {require('./assets/cake.jpeg')} style={{width : 300, height : 300}} />
      </View>
    )
  }
}

const App: () => React$Node = () => {
  return (
    <>
      <View style = {styles.container}>
        <Text style = {styles.hello}>Hello World!</Text>
        <Photo />
      </View>
    </>
  );
};
```
* 똑같은 결과 화면이 보입니다. 


```javascript
class Photo extends Component {
  render () {
    let img = '';
    if (this.props.type === 'one') {
      img = require('./assets/cake.jpeg');
    } else if (this.props.type === 'two') {
      img = require('./assets/perfum.jpeg');
    }
    return (
      <View>
        <Image source = {img} style={{width : 300, height : 300}} />
      </View>
    )
  }
}

const App: () => React$Node = () => {
  return (
    <>
      <View style = {styles.container}>
        <Text style = {styles.hello}>Hello World!</Text>
        <Photo type = 'one'/>
        <Photo type = 'two'/>
      </View>
    </>
  );
};
```

![image](https://user-images.githubusercontent.com/57790541/95009662-ca8f1800-065e-11eb-867a-3d19c8628aef.png)


* 각각 다른 사진이 화면에 출력되는 것을 확인할 수 있습니다. 

<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
