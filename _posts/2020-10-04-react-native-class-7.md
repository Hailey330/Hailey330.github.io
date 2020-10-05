---
layout: 'post'
title: 'React Native Stack 네비게이션'
description: '7. React Native 의 핵심인 네비게이션 알아보기 첫번째'
date: 2020-10-04 19:47
categories:
  - ReactNative
tags:
  - ReactNative
  - Navigation
---

# Stack Navigation
> React Navigation vs React Native Navigation

네비게이션 컴포넌트를 사용할 때 어떤 네비게이션을 사용하고 있는지 꼭 숙지를 한 다음에 사용해야 합니다.   
React Native Navigation 은 성능이 뛰어나지만 사용하기에 불편한 점이 있습니다. 


React Navigation 컴포넌트를 어떻게 사용하는지 알아봅시다. 


## 컴포넌트 설치하기 
[공식문서](https://reactnative.dev/docs/navigation)를 보면서 따라해봅시다. 

```
$ npm install @react-navigation/native @react-navigation/stack
```

* Expo 사용할 때 
```
$ expo install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view
```

* React Native CLI 사용할 때
```
$ npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view
```

```
$ cd ios
$ pod install
$ cd ..
```
<br/><br/>


## 컴포넌트 세팅하기
설치가 완료되면 상단에 아래의 코드를 차례대로 넣어줍니다. 
```javascript
import 'react-native-gesture-handler';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen
          name="Home"
          component={HomeScreen}
          options={{ title: 'Welcome' }}
        />
        <Stack.Screen name="Profile" component={ProfileScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};
```

* 이동할 네비게이션 페이지를 각각 생성해줍니다. 

```javascript
function HomeScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>HomeScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.navigate('Profile')}></Button>
    </View>
  )
}

function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
    </View>
  )
}

const App: () => React$Node = () => {
  return (
    <>
      <NavigationContainer>
        <Stack.Navigator>
          <Stack.Screen
            name="Home"
            component={HomeScreen}
            options={{ title: 'Welcome' }}
          />
          <Stack.Screen name="Profile" component={ProfileScreen} />
        </Stack.Navigator>
      </NavigationContainer>
    </>
  );
};
```

## 실행화면

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMjgz/MDAxNjAxODE3MjE5ODMy.KvCnHqRlNaW_Z4I0opLXFzfJGsCLkQXFvKCa7bVT9sgg.Rg0UQrFXd0EfLkkBrRnAf2SeluTNja64UrdOXXeMklYg.GIF.kid0739/Oct-04-2020_22-12-58.gif?type=w966)
* 네비게이션 컴포넌트로 간단하게 페이지 이동이 가능해졌습니다. 


# Navigate vs Push 


1. `navigation.navigate`
자기 자신에서 자기 자신의 페이지로 navigate 하게 되면 아무런 반응이 없습니다. 

```javascript
function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.navigate('Profile')}></Button>
    </View>
  )
}
```
![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMTA5/MDAxNjAxODE3ODQ4NDQ5.QOfTnd_exyPGU-um9ex6jASUJecOSN8RZed2MR7M2Lgg.NU1mS7FuzMB3yp8TYP1b8yJnL5bvr-HbtmKIj6WqEPgg.GIF.kid0739/Oct-04-2020_22-22-56.gif?type=w966)

* Profile 에서 Profile 페이지로 이동하는 코드로, 버튼을 누르면 아무런 동작이 없습니다. 
<br/>

```javascript
function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
      <Button title = "홈페이지로 이동" onPress={() => navigation.navigate('Home')}></Button>
    </View>
  )
}
```
![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMjE0/MDAxNjAxODE3OTU3MjM0.wdeNdT9ccuSTJdtflyS0H-YXq0Ffp_4oDLqL_2JAceYg.pP1fxTiaN2rFMQhtxCXnunJlYR_nnA9aG9uyYUWCYdcg.GIF.kid0739/Oct-04-2020_22-25-31.gif?type=w966)

* Home 에서 Profile, Profile 에서 Home 페이지로 이동하는 코드는 잘 이동하는 것을 확인할 수 있습니다.  
<br/>

2. `navigation.push`
push 사용시, 자기 자신을 계속 호출할 수 있습니다. 노트처럼 한 장씩 위에 얹혀진다고 생각하면 됩니다. 

```javascript
function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.push('Profile')}></Button>
    </View>
  )
}
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMTIz/MDAxNjAxODE4MTEyNzE2.tW33Ad-YysZ6der5yS0s8A6XAJWYr4HJPmfeepT1x9Qg.AgBq9j4F5NY8HaUbdWitRxca4CuahmyJKO1wslsiv8kg.GIF.kid0739/Oct-04-2020_22-28-13.gif?type=w966)

* Profile 에서 Profile 페이지로 이동하는 것이 가능해집니다. 새로운 페이지를 계속해서 쌓는다고 보면 됩니다. 
<br/><br/>


# Going Back vs PopToTop

1. `navigation.goBack`
한 페이지씩 뒤로 가기가 구현됩니다. 


```javascript
function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.push('Profile')}></Button>
      <Button title = "Go Back" onPress={() => navigation.goBack()}></Button>
    </View>
  )
}
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMTcg/MDAxNjAxODE4NTA0NzM5.sNO2Coh2mzwoBcs9uDNG70rngMIglA__75VeI7EeyxYg.opDF0kar4XOIFr_Z0n4LI4Hb4tOHRDBFMATQGN_cRyog.GIF.kid0739/Oct-04-2020_22-34-24.gif?type=w966)
<br/>

2. `navigation.popToTop`
한 번에 루트 페이지까지 뒤로 가기가 가능해집니다.


```javascript
function ProfileScreen({navigation}) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>ProfileScreen 입니다.</Text>
      <Button title = "프로필 페이지로 이동" onPress={() => navigation.push('Profile')}></Button>
      <Button title = "popToTop" onPress={() => navigation.popToTop()}></Button>
    </View>
  )
}
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDRfOTAg/MDAxNjAxODE5MTcwNDYx.cpUk1-BDrYgVdgjo7SEjy_zaMobN8-BkIH2wfUbIMJsg.gFjMU6RdQtgmGWz3a_vsEJP2XeVMqYe3SKJnyDRsp3Ug.GIF.kid0739/Oct-04-2020_22-45-43.gif?type=w966)
<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
