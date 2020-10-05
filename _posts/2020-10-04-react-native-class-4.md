---
layout: 'post'
title: 'React 기본 - State'
description: '4. React 기본 State 에 대하여'
date: 2020-10-04 16:30
categories:
  - ReactNative
tags:
  - ReactNative
---

# State? 
글로벌 변수 개념으로, 컴포넌트 내에서 값을 변경하거나 지정할 때 State 를 사용합니다.   
* 전역적인 상태 값을 유지하고 싶을 때, 유지된 값을 변경하고 싶을 때 사용합니다.   


State 의 초기 설정과 값 변경을 익혀봅시다. 


* constructor 를 이용할 때는 반드시 props 파라미터를 가져와서 super 에 props 를 지정해줘야 합니다. 

```javascript
class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      address : '부산시 어쩌구'
    }
  }

  render () {
    return (
      <>
        <View style = {styles.container}>
          <Text style = {styles.hello}>Hello World!</Text>
          <Image source = {require('./assets/cake.jpeg')} style={{width : 300, height : 300}} />
          
          <Text> {this.state.address}</Text>
          <Button title = {'나의 주소 출력'} />
        </View>
      </>
    );
  }
};
```


![image](https://user-images.githubusercontent.com/57790541/95010099-b00a6e00-0661-11eb-94e0-899029eeabba.png)


* 주소 출력 버튼을 눌렀을 때, 주소 값이 뜨도록 설정해봅시다. 
* 리셋하기 버튼도 같이 구현해봅시다.

```javascript
class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      address : ''
    }
  }

  writeAddress = () => {
    this.setState({
      address : '부산시 어쩌구'
    }) 
  }

  writeReset = () => {
    this.setState({
      address : ''
    }) 
  }

  render () {
    return (
      <>
        <View style = {styles.container}>
          <Text style = {styles.hello}>Hello World!</Text>
          <Image source = {require('./assets/cake.jpeg')} style={{width : 300, height : 300}} />
          
          <Text> {this.state.address}</Text>
          <Button title = {'주소 보여줘'} onPress = {this.writeAddress}/>
          <Button title = {'리셋하기'} onPress = {this.writeReset}/>
        </View>
      </>
    );
  }
};
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMjE4/MDAxNjAxNzk4NDMwMzE0.u7V6l_qnPvZ4DUlZwHguN1sfa2oujStHBU8m8ef2Misg.o77YiLh8TKIb-lQ-pxnP1IH-tbpBoi_CAG-it8lrF0gg.GIF.kid0739/Oct-04-2020_16-59-56.gif?type=w966)


* 주소가 뜨는 동시에 `alert` function 을 추가해봅시다.  

```javascript
writeAddress = () => {
    this.setState({
      address : '부산시 어쩌구'
    }, function() {
      alert('주소 불러오기 완료');
    })
  }
```


![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMjY5/MDAxNjAxNzk4NzI5NDI1.6OxO4y6ODOLaFBfEN37YkifWrcNudMAoZIwdRHpQsswg.Gt_i0IFZSAo6hYvstwD1uFJ3KMbJud7hvwGtiVSPSukg.GIF.kid0739/Oct-04-2020_17-04-13.gif?type=w966)
<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
