---
layout: 'post'
title: 'React Native 네비게이션 파라미터 넘기기(1)'
description: '8. React Native 의 핵심인 네비게이션 알아보기 두번째'
date: 2020-10-04 22:49
categories:
  - ReactNative
tags:
  - ReactNative
  - Navigation
---

# Passing Parameters
보통 앱을 사용하면서 페이지를 이동할 때, 아무런 데이터없이 화면 전환이 되는 경우는 극히 드문 일입니다.   
화면과 화면 간의 이동에서는 서로에게 필요한 데이터가 있습니다.   


[공식문서](https://reactnavigation.org/docs/params) 를 참고하면서 따라해봅시다.

```javascript
function HomeScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>HomeScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.navigate('Profile', {
        itemId: 86,
        otherParam: 'anything you want here',
      })}></Button>
    </View>
  )
}
```


* `HomeScreen()` 의 버튼에서 넘길 데이터를 넣어줍니다.   
`itemId`, `otherParam` 값을 Profile 페이지로 넘겨봅시다. 


```javascript
function ProfileScreen({ route, navigation}) {

  const { itemId } = route.params;
  const { otherParam } = route.params; // const otherParam = route.params.otherParam;

  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>

      <Text>itemId: {JSON.stringify(itemId)}</Text>
      <Text>otherParam: {JSON.stringify(otherParam)}</Text>

    </View>
  )
}
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMTAg/MDAxNjAxODIwNTcyNDM5.xKupdfIxnynnWHnzleo5hCVRE8zut1Gx_FyaEZfbZs8g.CFFgMqEuFWexvqckktaz5_GicdOvT9KerouEKc2_G-Ag.GIF.kid0739/Oct-04-2020_23-09-13.gif?type=w966)

* `HomeScreen()`에서 넘긴 데이터 값이 제대로 넘어온 것을 확인할 수 있습니다. 


# initialParams 
```javascript
const App: () => React$Node = () => {
  return (
      <NavigationContainer>
        <Stack.Navigator>
          <Stack.Screen
            name="Home"
            component={HomeScreen}
            options={{ title: 'Welcome' }}
          />
          <Stack.Screen 
            name="Profile" 
            component={ProfileScreen} 
            initialParams={{ itemId: 42 }}/>
        </Stack.Navigator>
      </NavigationContainer>
  );
};
```
* `Stack.Screen` 에 `initialParams = {data}` 를 추가해주면 데이터를 넘길 수 있습니다.   
다만, initial 초기 값이기 때문에 위에서 다른 데이터를 넘기면 없어집니다. 

<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
