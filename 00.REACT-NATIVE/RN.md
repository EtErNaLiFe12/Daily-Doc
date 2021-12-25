# REACT NATIVE 관련

## React-native start
react-native init ReactNativeTodos
npx react-native init AwesomeProject
npx react-native init AwesomeProject --version X.XX.X

## devices check
adb devices

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

npm i @react-native-community/async-storage

```js
// import 하기
import { ASYNC_PARAMETER } from "@common/xxxxxx";
import AsyncStorage from "@react-native-community/async-storage";

// /common/xxx.js
export const ASYNC_PARAMETER = {
  FIRST_APP: 'FirstLaunch'
};

// /App.js
useEffect( async () => {
    try {
      const FirstLaunched = await AsyncStorage.getItem(ASYNC_PARAMETER.FIRST_APP)
      console.log('check', FirstLaunched)
      if (FirstLaunched === null) {
        console.log('setFirstLaunch')
        AsyncStorage.setItem(ASYNC_PARAMETER.FIRST_APP, "true")
        const eventAttr = new AdbrixRm.AttrModel();
          eventAttr.setAttrs("firstLaunch",FirstLaunched)
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
  console.log('컴포넌트가 나타남');
  // 실행 할 함수
  return () => {
    console.log('컴포넌트가 사라짐'); // clean-up 함수
  }
}, []) // 빈배열 또는 실행 함수 이름 삽입 - 빈 배열을 default값으로 넣어줘야 최초 한번만 실행 (안 넣어주면 두세번 실행됨)

// 실행 할 함수 이름 삽입시 변경 또는 수정 될때마다 실행 함. 그 전까지는 최초 1번만 실행함.
```

## HTMLVIEW

```js
  <HTMLView html={note}/>
```


## screen width & height 값 가져오기

```js
export const S_HEIGHT = Dimensions.get('screen').height;  //screen은 핸드폰의 상부 bar영역을 포함시킴
export const S_WIDTH = Dimensions.get('screen').width;
//--------------------------------------------------------
export const S_WIDTH = Dimensions.get('window').width; // window는 핸드폰의 상부 bar영역을 포함시키지 않음
export const S_WIDTH = Dimensions.get('window').height;
```

## stylesheet 사용법
```js
export default const test () => {
  return <View style={{styles.container}}></View>
}


const styles = StyleSheet.create({
  container: {
    width: 214,
    paddingLeft: 15,
    paddingRight: 20,
    paddingVertical: 20,
    justifyContent: "center",
    backgroundColor: "#fff",
    borderStyle: "solid",
    borderWidth: 1,
    borderColor: "#fb5849"
  }
})
```

## shadow(ios/android)

```js
// ios shadow style 영역
style={{ shadowColor: "#000",
          shadowOffset: {
              width: 0,
              height: 1,
          },
          shadowOpacity: 0.07,
          shadowRadius: 12,
          // android shadow style 영역
          elevation: 2,}}> 
```

## shadow style

```js
const styles = StyleSheet.create({
  textInput: {
    width: '100%',
    height: 70,
    paddingTop: 5,
    paddingBottom: 5,
    backgroundColor: "#ffffff",
    shadowColor: "#000", // ios
    shadowOffset: {
      width: 0,
      height: 2,
    },
    shadowOpacity: 0.25,
    shadowRadius: 3.84,
    elevation: 5, // android
}
```



## Progress Bar#1 - react native

```js
import { ProgressBar } from 'react-native-paper';

<ProgressBar 
  progress={0.5} 
  color={'#e4a8b0'} // progressbar color
  style={{ backgroundColor: '#f4f4f4'}} // progressbar background color(applied with inline style)
/>
```

## build clean
cd android
./gradlew clean

## build - apk 만들기
cd android
./gradlew clean assembleRelease


## Progress Bar#2 - react native

https://github.com/oblador/react-native-progress

 ## react native 디버깅시
 - metro에서 d 누름 -> debugging mode 실행
 - 자동으로 웹사이트 디버깅 모드 실행됨
 ## react-native stack navigation

npm install @react-navigation/native @react-navigation/native-stack

- If you have a bare React Native project, install the dependencies with npm:

npm install react-native-screens react-native-safe-area-context

- For iOS with bare React Native project, make sure you have Cocoapods installed. Then  
  install the pods to complete the installation:

  cd ios
  pod install
  cd ..

npm i react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view

- vector-icons
  npm install --save react-native-vector-icons

  react-native link react-native-vector-icons

ios는 직접 설정 해줘야 함. (중복오류 발생됨)...

- drawer navigation
  npm install --save @react-navigation/drawer

- 하단 navigation
  npm install --save @react-navigation/bottom-tabs

- material bottom tab navigation
  npm install --save @react-navigation/material-bottom-tabs react-native-paper

---
## Axios

npm install --save axios

https://wickies.tistory.com/101?category=768093

https://post.naver.com/viewer/postView.naver?volumeNo=27835820&memberNo=2490752

https://www.youtube.com/watch?v=nrxzK_ky3uc&t=335s

http://yoonbumtae.com/?p=658
x
https://aljjabaegi.tistory.com/561?category=971831

https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=leety72&logNo=221679960960

---

## react native toast animation package

https://github.com/calintamas/react-native-toast-message/blob/e1c2117b7496a58adde7081e1eaa0867aa6d5d6c/docs/api.md

## react native audio player package

https://www.npmjs.com/package/react-native-track-player

## react-native modal

<!-- modal에서 modal로 이어지는 process는 권장하지 않음 -->
https://reactnativeseoul.org/t/modal/737/2

To open another modal from main or first modal that activated, should close first modal in advance.

for instance, if using modal by change the state with react hook - useState(),

then, put false in useState value for close the modal and then open another

modal. 

but it won't work by only using true and false in order to close and open the modal.

```js
setIsModal(false);
setIsModal2(true);
```
<!-- Countermeasure -->

use setTimeout func. in  for make delay more than 500ms.

setTimeout func wouldn't need in first modal for close.

just need for other one.

```js
const example = () => {
  setIsModal(false);
  setTimeout(()=> {
    setIsModal2(true);
  }, 500);
}
```

## stack navigation icons

https://www.npmjs.com/package/@fortawesome/react-native-fontawesome

npm i --save react-native-svg # **
npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/react-native-fontawesome

Visit fontawesome.com/icons to search for free and Pro icons

npm i --save @fortawesome/free-brands-svg-icons
npm i --save @fortawesome/free-regular-svg-icons

npm i --save @fortawesome/free-solid-svg-icons

npm i --save react-native-svg-transformer

## react native svg auto link error 

Invariant Violation: requireNativeComponent: "RNSVGPath" was not found in the UIManager

https://github.com/react-native-svg/react-native-svg/issues/834

<!-- in MainApplication.java file -->
```java
@Override
  protected List<ReactPackage> getPackages() {
    @SuppressWarnings("UnnecessaryLocalVariable")
    List<ReactPackage> packages = new PackageList(this).getPackages();
    // Packages that cannot be autolinked yet can be added manually here, for example:
    // packages.add(new MyReactNativePackage());
    packages.add(new SvgPackage());
    return packages;
  }
```

## 외부 폰트 적용하기 

https://velog.io/@ziyoonee/React-Native-custom-font-%EC%A0%81%EC%9A%A9


## react native icon 삽입

<!-- android icon generator site-->
http://romannurik.github.io/AndroidAssetStudio/icons-launcher.html#foreground.type=text&foreground.text.text=JB&foreground.text.font=Comic%20Neue&foreground.space.trim=1&foreground.space.pad=0.35&foreColor=rgb(255%2C%20255%2C%20255)&backColor=rgb(33%2C%20150%2C%20243)&crop=0&backgroundShape=square&effects=elevate&name=ic_launcher
<!-- android -->
android/app/src/main/res 에 있는 폴더에 icon 삽입

ic_launcher.xml
ic_launcher_round.xml

<!-- ios icon generator site -->
https://appicon.co/
<!-- ios -->
app이름/Images.xcassets 에서 설정 할 것

