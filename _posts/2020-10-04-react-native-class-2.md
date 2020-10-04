---
layout: 'post'
title: 'React Native 텍스트 출력하기'
description: '2. React Native 프로그래밍은 Hello World 출력이 기본'
date: 2020-10-04 13:10
categories:
  - ReactNative
tags:
  - ReactNative
---

# Hello World 실행하기
## 자바스크립트 프레임워크, 모바일 개발
전에 Android 와 IOS 각각 개발할 때는 시간이 많이 들고 같은 내용을 다른 소스 코드로 짜야하는 불편함이 컸습니다.   
그러던 중 하나의 소스로 Android, IOS 를 한 번에 개발할 수 있지 않을까 하고 나왔던 프레임워크들이 델파이, Visual Studio C# 등이 나왔지만 둘 다 간단하지 않았습니다.    
이에 반해 React Native 는 ReactJs 에서 사용했던 문법 그대로를 사용할 수 있다는 점에서 큰 메리트가 있기 때문에 지금도 많이 사용하는 프레임워크입니다.  


## Expo CLI vs React Native CLI
#### Expo CLI의 장단점  
* 편리한 배포와 디버깅
* Expo 에서 제공하는 편리한 기능 사용 
* 추가적인 Native 코드 작성 불가능 (eject 를 통해 가능하긴 하지만 힘들겁니다..)

#### React Native CLI 장단점
* Xcode, Android Studio 를 통해서 Native 코드 확장 가능 (카카오톡 연동)   
직접 개발을 하다보면 카카오 연동과 같은 기능을 추가할 때가 있는데, Native 폴더가 생성되지 않는 Expo 로는 한계가 있습니다.   
Expo 자체에서 제공하는 기능이 아니라면 실질적으로 연동하기가 굉장히 어렵습니다.   
그렇지만 React Native CLI 는 융합하기가 용이합니다.   
때문에 지금부터 실행할 코드들은 React Native CLI 를 사용할 것입니다. 

## 실행하기
NativeTest 폴더를 열어서 화면을 책임지는 App.js 분석해봅시다.   

* 코드 수정 후 새로고침 `command + R`
* 코드 수정 후 알아서 새로고침 기능 `command + D` - Enable Live Reload 적용하면 코드 수정했을 때 바로 반영이 됩니다. (제가 실행한 iPhone 11 버전에서는 설정을 따로 하지 않아도 바로 새로고침이 되네요.)


![image](https://postfiles.pstatic.net/MjAyMDEwMDRfMTIy/MDAxNjAxNzg4OTk1NDMw.sGojKdOlewQZq7ipLfPMWxjgRqgM5r30zNrVASOjqzsg.z2MoI80VNwzcujVkSHjsAwaybNMuFdEN_zNRO2Yrwr4g.PNG.kid0739/Screenshot_at_Oct_04_14-21-31.png?type=w966)
* Hello World 텍스트를 출력하고 간단한 스타일 적용까지 해봤습니다.

<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
