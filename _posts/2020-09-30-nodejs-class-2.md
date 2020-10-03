---
layout: 'post'
title: 'JavaScript 기본 문법'
description: '2. Node.js 를 위한 자바스크립트 기본'
date: 2020-09-30 15:32
categories:
  - Programming
tags:
  - Nodejs
  - JavaScript
---


# Number Data type, String Data type
컴퓨터를 사용하는데 있어서 가장 중요한 점은 '데이터를 어떻게 처리할 것인가?' 입니다.   
어떠한 데이터가 있는지, 각각의 데이터는 어떻게 처리해야 하는지에 대해서 자바스크립트 언어는 `Number`, `String`, `Boolean`, `Array` 등 형식을 지정해뒀습니다.
<br/><br/>


# 변수의 형식과 활용
변수의 기본 형식 `var a = 1;`

변수를 사용해야 하는 이유   
1. 데이터의 이름을 붙여 가독성을 좋게 만들어 줍니다.   
2. 변수를 이용해 중복되는 코드를 제거할 수 있습니다.   
<br/><br/>


# Template Literal
정보를 표현하는 방법으로, 여러 줄로 이루어진 문자열의 표현과 문자의 치환을 쉽게 할 수 있는 기능을 제공합니다. 

```javascript
var name = 'hongcha';
// String Literal
var letter = 'Dear ' + name + ' Hello! ' + name;
// Template Literal
var letter = `Dear ${name} Hello! ${name}`;
```
<br/><br/>


# 배열과 반복문
배열(Array)은 서로 연관된 데이터를 정리정돈하는 도구입니다. 

```javascript
var arr = ['a', 'b', 'c', 'd'];
console.log(arr[1]);
arr[2] = 3;
console.log(arr);
console.log(arr.length);
arr.push('e');
console.log(arr);
```
```
출력 결과
b
[ 'a', 'b', 3, 'd' ]
4
[ 'a', 'b', 3, 'd', 'e' ]
```
<br/>

```javascript
var number = [1, 400, 12, 34, 5];
var i = 0;
var total = 0;
while(i < number.length) {
    total = total + number[i];
    i = i + 1;
}
console.log(`total : ${total}`);
```
```
출력 결과
total : 452
```
<br/><br/>


# 함수의 입출력
### 입력(Input)
* 파라미터(Parameter) : 입력되는 형식
* 인자(Argument) : 형식에 맞게 들어간 값

### 출력(Output)
* URL 을 통해서 입력 값을 주고 출력 값을 얻습니다. 


왜 함수를 만들어야 할까요? 
1. 반복되는 코드들을 함수로 만들어 실행하면 가독성이 좋아집니다. 
2. 코드 추가하는 것이 쉬워집니다. 따라서 유지보수 편의성이 높아집니다. 

```javascript
function sum(first, second) { // parameter(매개변수)
    console.log(first + second);
}

// 함수의 입력 
sum(2, 4); // argument(인자)
```

```javascript
function sum(first, second) {
    return first + second; 
}

console.log(sum(2, 4)); 
```
* return 을 사용하게 되면 함수의 출력과 동시에 종료됩니다. 
<br/><br/>


***
## 참고
* [생활코딩 Node.js](https://opentutorials.org/course/3332)
