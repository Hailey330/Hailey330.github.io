---
layout: 'post'
title: 'React Native 레이아웃과 flex box'
description: '6. React Native 에서 중요한 레이아웃과 flex box 알아보기'
date: 2020-10-04 19:47
categories:
  - ReactNative
tags:
  - ReactNative
---

# flex 
flex 는 레이아웃을 꾸미기 위한 방법입니다.    
전체 영역을 잡고 그 영역에 대해서 flex 비율대로 레이아웃을 꾸미는데, 일정한 비율별로 레이아웃을 구성할 수 있습니다.   
프로젝트를 만들 때 구성을 잡고 세부적으로 들어가기 때문에 전체적인 구성 잡는데 있어 굉장히 중요합니다.  

```javascript
class App extends Component {
  render() {
    return (
      <View style = {styles.container}>
        <View style={{ flex: 1, backgroundColor: 'beige' }}>
        </View>
        <View style={{ flex: 2, backgroundColor: 'orange' }}>
        </View>
        <View style={{ flex: 3, backgroundColor: 'lightblue' }}>
        </View>
      </View>
    );
  }
};

const styles = StyleSheet.create({
  container: {
    flex: 1
  }
});
```

![image](https://user-images.githubusercontent.com/57790541/95014064-51ec8380-067f-11eb-9f3c-c1410cebc187.png)

* 방향을 특별하게 지정해주지 않으면 디폴트 값으로 'column' 세로로 적용됩니다. 
<br/>

```javascript
class App extends Component {
  render() {
    return (
      <SafeAreaView style = {styles.container}>
        <View style={{ width: 50, height:50, backgroundColor: 'beige' }}>
        </View>
        <View style={{ width: 50, height:50, backgroundColor: 'orange' }}>
        </View>
        <View style={{ width: 50, height:50, backgroundColor: 'lightblue' }}>
        </View>
      </SafeAreaView>
    );
  }
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: 'row-reverse'
  }
});
```
* `SafeAreaView` 를 사용하게 되면 알아서 상단의 바를 제외하고 그림을 그려줍니다.
* `flexDirection: 'row-reverse'` 순서를 거꾸로 뒤집어서 그림을 그려줍니다. 

![image](https://user-images.githubusercontent.com/57790541/95014237-801e9300-0680-11eb-90a2-88e6c8da2616.png)


```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    flexDirection: 'column-reverse'
  }
});
```


![image](https://user-images.githubusercontent.com/57790541/95014445-d213e880-0681-11eb-9247-2b6048811669.png)
<br/><br/>

***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
