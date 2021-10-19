# REACT NATIVE 관련

## .toFIxed - 소수점 자리 위치

```jsx
<View>
  <Text>{(data.length / 60).toFixed(0) + `${":"}` + (data.length % 60).toFixed(0)}</Text>
</View>
```

## Text 속성

```jsx
<View>
  <Text
    numberOfLines={1} // 몇번쨰 줄까지 보이게 할 것인지
    ellipsizeMode="tail" // 위에 지정한 n번째 줄에서 ...을 보이게 함 
  ></Text>
</View>
``` 

## AsyncStorage 

```js
// import 하기
import { ASYNC_PARAMS } from "@common/xxxxxx";
import AsyncStorage from "@react-native-community/async-storage";

// /common/xxx.js
export const ASYNC_PARAMS = {
  FIRST_APP_SETUP: 'keyFirstLaunch'
};

// /App.js
useEffect( async () => {
    try {
      const isFirstLaunched = await AsyncStorage.getItem(ASYNC_PARAMS.FIRST_APP_SETUP)
      console.log('chk', isFirstLaunched)
      if (isFirstLaunched === null) {
        console.log('setFirstLaunch')
        AsyncStorage.setItem(ASYNC_PARAMS.FIRST_APP_SETUP, "true")
        const eventAttr = new AdbrixRm.AttrModel();
          eventAttr.setAttrs("firstLaunch",isFirstLaunched)
        AdbrixRm.commerceViewHome(eventAttr);
      }
    } catch (error) {
        console.log(' [chk first launch] :' + error);  
    }

  },[])

```

## useEffect

```js

useEffect(() => {
  // 실행 할 함수
}, []) // 빈배열 또는 실행 함수 이름 삽입 - 빈 배열을 default값으로 넣어줘야 최초 한번만 실행 (안 넣어주면 두세번 실행됨)

// 실행 할 함수 이름 삽입시 변경 또는 수정 될때마다 실행 함. 그 전까지는 최초 1번만 실행함.

```

