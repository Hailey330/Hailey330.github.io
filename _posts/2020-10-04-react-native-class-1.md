---
layout: 'post'
title: 'React Native 알아가기'
description: '1. React Native 설치에서 실행까지'
date: 2020-10-04 02:50
categories:
  - ReactNative
tags:
  - ReactNative
---

# React Native? 
리액트 네이티브는 페이스북이 개발한 오픈 소스 모바일 애플리케이션 프레임워크입니다.   
리액트를 기반으로 '네이티브 앱'을 제작할 수 있으며, 안드로이드, IOS, 웹 등 애플리케이션을 개발하기 위해 사용합니다.   
네이티브 개발이기 때문에 HTML 태그와 CSS를 사용할 수 없습니다. 

## 왜 React Native 를 사용할까? 
1. 개발하기 쉽습니다.
2. 하나의 소스로 IOS, Android, Native App까지 동시에 개발할 수 있습니다. (멀티 지원!)
<br/><br/>


# React Native 설치하기
React Native 를 설치하는 방법은 2가지로, Expo 를 이용하는 방식과 React Native 를 이용하는 방식이 있습니다. 


## Expo 로 설치하기
#### Node.js 설치하기
설치하기 전에 Node.js 가 설치되어 있는지 버전을 확인합니다.  
```
$ node -v
v12.18.4
```


#### CLI 설치하기
```
$ npm install -g expo-cli
```


#### Project 실행하기 
```
$ expo init expoTest
$ cd expoTest
$ npm start
```
![image](https://user-images.githubusercontent.com/57790541/94998844-e9a29100-05ef-11eb-9377-63df0682dfc9.png)

![image](https://user-images.githubusercontent.com/57790541/94998903-5f0e6180-05f0-11eb-83ec-5eb627e2c543.png)


> 만약 Tunnel ready 가 뜨지 않을 경우

![image](https://user-images.githubusercontent.com/57790541/94998875-1656a880-05f0-11eb-8c75-9b8c5a914c08.png)
* 위와 같이 Starting Metro Bundler 에서 멈출 경우에는 `npm start` 대신 `expo-cli start --tunnel` 으로 실행하면 됩니다. 혹은 PC 재부팅을 하면 해결이 됩니다. 


#### 가상 실행
Expo 에서는 Android 애뮬레이터를 실행할 수 있고 IOS 애뮬레이터도 실행할 수 있습니다. 

1. 안드로이드 스튜디오 설치하기   
설치가 완료되면, 안드로이드 스튜디오 툴을 켜고 Configure 의 SDK Manager 에서 Android 9.0 이상 설치를 진행합니다.   
다음에 AVD Manager 에서 다음과 같이 진행합니다. 

![image](https://user-images.githubusercontent.com/57790541/94999165-8bc37880-05f2-11eb-8447-f9e3466e2015.png)
![image](https://user-images.githubusercontent.com/57790541/94999262-43588a80-05f3-11eb-9162-7e9f9c539e4c.png)
![image](https://user-images.githubusercontent.com/57790541/94999289-61be8600-05f3-11eb-9ae6-ffb3c8ec784c.png)
![image](https://user-images.githubusercontent.com/57790541/94999308-73079280-05f3-11eb-8288-9287c9ea4c78.png){: width="300" height="300"}


* 설치가 완료된 후에 Expo 로 돌아가 Android 애뮬레이터 실행하기

![image](https://user-images.githubusercontent.com/57790541/94999776-9a139380-05f6-11eb-9420-7673b3a120aa.png)
![image](https://user-images.githubusercontent.com/57790541/94999718-4bfe9000-05f6-11eb-8c39-6ecb7912086d.png)
<br/>


2. Xcode 설치하기   
맥 App Store 에서 Xcode 검색 후 설치합니다.   
설치에 꽤 오랜 시간이 걸립니다. (저는 30분 이상 걸렸습니다..:sweat_smile:)


```
# 아이폰
$ npm run ios
# 안드로이드
$ npm run android
```

![image](https://user-images.githubusercontent.com/57790541/95006258-84758c80-063d-11eb-9d40-237baa1d7fdf.png)
![image](https://user-images.githubusercontent.com/57790541/95006358-bb986d80-063e-11eb-921d-300af1c33557.png)
* IOS 애뮬레이터가 실행되는 모습입니다. 
<br/><br/>


#### Device 실행
시뮬레이터에서만 개발을 하고, 배포할 때만 기기에서 실행하다가는 오류를 마주칠 가능성이 있습니다.   
시뮬레이터에서 동작이 잘된다고 해도 실제 기기에서는 어떻게 동작하는지 확인을 계속 해봐야 합니다.   

1. 안드로이드 Expo 다운로드 후 실행하기 
2. 아이폰 Expo Client 다운로드 후 실행하기
<br/><br/>


## React Native CLI 로 설치하기
#### Node, Watchman, JDK 설치하기 (Mac 기준)
```
$ brew install watchman
$ brew tap AdoptOpenJDK/openjdk
$ brew cask install adoptopenjdk8
```

#### React Native CLI 설치하기
```
$ npm install -g react-native-cli
```

#### Project 생성하기
```
$ react-native init nativeTest
$ cd nativeTest
$ react-native run-ios
$ react-native run-android
```
![image](https://user-images.githubusercontent.com/57790541/95007232-577aa700-0648-11eb-9ac0-1e43d1dff2f7.png)
* Android, IOS 폴더가 잘 생성된 것을 확인할 수 있습니다.   
2가지 폴더가 생성됨으로써 실제 Android, IOS 의 Native 코드를 삽입할 수 있습니다.   
Expo 에서는 Expo 에서만 제공하는 기능만 사용해야 하는 단점이 있습니다. 


#### Project 실행하기 (Simulator)

![image](https://user-images.githubusercontent.com/57790541/95007345-9c530d80-0649-11eb-93d3-a4b397a658de.png)
* 제대로 잘 실행이 됩니다. 

<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
* [React Native 공식문서 참고](https://reactnative.dev/docs/environment-setup)
