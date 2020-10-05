---
layout: 'post'
title: 'React Native 네비게이션 파라미터 넘기기(2)'
description: '9. React Native 의 핵심인 네비게이션 알아보기 세번째'
date: 2020-10-04 23:18
categories:
  - ReactNative
tags:
  - ReactNative
  - Navigation
---

# useState vs useEffect
1. useState

* 클래스 기반 컴포넌트 : this.state   
class 컴포넌트에서는 `constructor` 를 정하고 함수를 정의해서 일반적인 자바스크립트 형식으로 함수 호출하고, `this.state` 이용해서 값을 정의합니다.   
간단한 상태 관리인데도 함수 기반 컴포넌트에 비해 복잡해서 오류가 발생하기 쉽고, 유지 보수가 힘듭니다. 


```javascript
class Hook extends Component {

    constructor(props){
        super(props);
        this.state = {
            name : 'hongcha'
        }
    }

    changeName = () => {
        this.setState({
            name : 'scone'
        });
    }

    render() {
        return (
            <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
                <Text>Hook 테스트입니다.</Text>
                <Button title = {'이름 변경하기'} onPress={() => this.changeName()} />
                <Text>안녕하세요 {this.state.name} 님!</Text>
            </View>
        );
    }
}
```


* 함수 기반 컴포넌트 : setState()
React Hooks 에서 제공하는 `useState()` 함수를 사용해서 초기 값을 설정해봅시다.   
`useState()` 함수는 배열을 리턴하는데 첫 번째 원소는 상태 값을 저장할 변수이고 두 번째 원소는 상태 값을 갱신할 때 사용할 수 있는 함수입니다. 
```javascript
const ['상태 값 저장 변수', '상태 값 갱신 함수'] = useState('상태 초기 값');
```


```javascript
const Hook: () => React$Node = () => {
    const [name, setName] = useState('hongcha');
    
    return (
        <>
            <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
                <Text>Hook 테스트입니다.</Text>
                <Button title = {'이름 변경하기'} onPress={() => setName('scone')} />
                <Text>안녕하세요 {name} 님!</Text>
            </View>
        </>
    );
};

const styles = StyleSheet.create({

});

export default Hook;
```

![image](https://postfiles.pstatic.net/MjAyMDEwMDVfMTYy/MDAxNjAxODIzOTYwMzkx.gR5sO-wFbT01LS4uX5XnuMP84cIJJSBhq4IUtPKLE5Eg.BGuAv-9O649UAa8ntqwf86hV0nV9GfHQSlV5h1Z7bj8g.GIF.kid0739/Oct-05-2020_00-05-42.gif?type=w966)

* 함수형 컴포넌트를 사용하게 되면 클래스형 컴포넌트보다 간결하게 코드를 짤 수 있습니다.
<br/>


2. useEffect
초기 값 세팅시 유용하게 사용하는 함수입니다.   
데이터 넘어왔는지 확인하는 이벤트를 계속해서 실시간으로 체킹합니다. 

* 함수 기반 컴포넌트 : setEffect()
React Hooks 에서 제공하는 `useEffect()` 함수를 사용해봅시다. 

```javascript
const Hook: () => React$Node = () => {
    const [name, setName] = useState('hongcha');

    const [loading, setLoading] = useState(true);
    const [users, setUsers] = useState([]);

    useEffect(() => {
        fetch("https://jsonplaceholder.typicode.com/users")
            .then((response) => response.json())
            .then((users) => {
                setUsers(users)
                setLoading(false)
            });
    });

    return (
        <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
            <Text>Hook 테스트입니다.</Text>
            <Button title={'이름 변경하기'} onPress={() => setName('scone')} />
            <Text>안녕하세요 {name} 님!</Text>
            <FlatList
                data={users}
                renderItem={({ item }) => <Text> { item.name } </Text>}
                keyExtractor={item => item.id}
            />
        </View>
    );
};
```

![image](https://user-images.githubusercontent.com/57790541/95046220-ba3e7200-071e-11eb-8f97-2a2c1b9cf6a7.png)


## Example
[공식문서](https://reactnavigation.org/docs/params/)에 있는 예제로 `useState` 와 `useEffect` 를 사용해봅시다. 


```javascript
import { StyleSheet, View, Text, Button, TextInput } from 'react-native';

function HomeScreen({ navigation, route }) {
  React.useEffect(() => {
    if (route.params?.post) {
      // Post updated, do something with `route.params.post`
      // For example, send the post to the server
    }
  }, [route.params?.post]);

  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Button
        title="Create post"
        onPress={() => navigation.navigate('CreatePost')}
      />
      <Text style={{ margin: 10 }}>Post: {route.params?.post}</Text>
    </View>
  );
}

function CreatePostScreen({ navigation, route }) {
  const [postText, setPostText] = React.useState('');

  return (
    <>
      <TextInput
        multiline
        placeholder="What's on your mind?"
        style={{ height: 200, padding: 10, backgroundColor: 'white' }}
        value={postText}
        onChangeText={setPostText}
      />
      <Button
        title="Done"
        onPress={() => {
          // Pass params back to home screen
          navigation.navigate('Home', { post: postText });
        }}
      />
    </>
  );
}

const App: () => React$Node = () => {
  return (
    <>
      <NavigationContainer>
        <Stack.Navigator mode="modal">
          <Stack.Screen name="Home" component={HomeScreen} />
          <Stack.Screen name="CreatePost" component={CreatePostScreen} />
        </Stack.Navigator>
      </NavigationContainer>
    </>
  );
};
```


* `route.params?.post` = `route.params?route.params.post : ''`   
삼항 연산자는 코드가 길어서 보기 쉽지 않습니다. 그래서 물음표 하나로 한번에 작성합니다. 


* 코드 알아보기
![image](https://user-images.githubusercontent.com/57790541/95048624-1d320800-0723-11eb-9606-b730b6f32ce0.png)
![image](https://user-images.githubusercontent.com/57790541/95048739-55d1e180-0723-11eb-804b-7a5ab72a191f.png)
<br/><br/>


***
## 참고
* [스피드잡스 유튜브 리액트 강좌](https://youtu.be/Sr5UOR4llXY)
