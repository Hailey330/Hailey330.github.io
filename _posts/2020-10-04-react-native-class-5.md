---
layout: 'post'
title: 'React 기본 - Style'
description: '5. React 기본 Style 에 대하여'
date: 2020-10-04 17:07
categories:
  - ReactNative
tags:
  - ReactNative
---

# Style 적용하기
## flexDirection
React Native 의 Style 코드는 CSS 와 흡사합니다. 


* 새 프로젝트 생성
```
$ react-native init nativeStyleEx
```


* 전체를 View 하나에 두고 사진의 오른쪽에 텍스트를 배치하기 위해서 `flexDirection: 'row'` 잡고 이미지 컴포넌트 하나, 텍스트 컴포넌트 하나씩 두는 코드를 작성해보겠습니다.  

```javascript
class App extends Component {
  render() {
    return (
      <View>
        <View style={styles.container}>
          <Image source={require('./assets/itsme.jpeg')} style={{ width: 150, height: 150 }} />

          <View style={{ flexDirection: 'column' }}>
            <View style={{ flexDirection: 'row' }}>
              <Text style={styles.title}>이름</Text>
              <Text style={styles.detail}>홍차</Text>
            </View>
            <View style={{ flexDirection: 'row' }}>
              <Text style={styles.title}>생일</Text>
              <Text style={styles.detail}>1993.03.30</Text>
            </View>
            <View style={{ flexDirection: 'row' }}>
              <Text style={styles.title}>취미</Text>
              <Text style={styles.detail}>수영하기</Text>
            </View>
            <View style={{ flexDirection: 'row' }}>
              <Text style={styles.title}>취향</Text>
              <Text style={styles.detail}>프렌치시크</Text>
            </View>
          </View>
        </View>
      </View>
    )
  };
};
```


```javascript
const styles = StyleSheet.create({
  container: {
    marginTop: 100,
    marginLeft: 20,
    flexDirection: 'row'
  },
  title: {
    marginLeft: 10,
    fontWeight: 'bold',
    color: 'gray',
    fontSize: 15
  },
  detail: {
    marginLeft: 10
  }
});
```


```javascript
// 하단에 컬러 박스 추가하기
<View style = {{width: 500, height: 100, backgroundColor: 'beige'}}></View>
```
<br/>

#### 실행 화면 
![image](https://user-images.githubusercontent.com/57790541/95013080-b9530500-0678-11eb-97a9-3ae54682d8c0.png)


![image](https://user-images.githubusercontent.com/57790541/95013221-de944300-0679-11eb-92c9-56fdd316bdb1.png)
<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
