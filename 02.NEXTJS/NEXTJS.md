## Nextjs start

node 설치 후 

npx create-next-app 폴더명

npx create-next-app@latest

First, run the development server:

```bash
npm run dev
# or
yarn dev
```
## Nextjs react-device-detect package 설치

<!-- 참고 github 주소 -->
https://github.com/duskload/react-device-detect

npm install react-device-detect --save

* android / ios 기종 판별 등
* 모바일 / 웹 판별 등

## semantic-ui-react package 가져오기
```bash
npm install semantic-ui-react semantic-ui-css
```
install 후 

```js
import 'semantic-ui-css/semantic.min.css'
```
## semantic-ui-react 사용하기

사이트-https://react.semantic-ui.com/

```js
// import를 통해 semantic-ui-react에서 가져오기
import { Menu } from "semantic-ui-react"

export default function Gnb(){
    const activeItem = "home";
    return (
      // 사이트 참조
        <Menu inverted>
        <Menu.Item
          name='home'
          active={activeItem === 'home'}
        //   onClick={this.handleItemClick}
        />
        <Menu.Item
          name='messages'
          active={activeItem === 'messages'}
        //   onClick={this.handleItemClick}
        />
        <Menu.Item
          name='friends'
          active={activeItem === 'friends'}
        //   onClick={this.handleItemClick}
        />
      </Menu>
    )
}
```

## API 받아오기

Axios 설치 요망

```bash
npm install axios
```
설치 후

```js
export default function Home() {
  //react hook 중 useState을 사용 하여 component 바뀌는 값 관리
  //초기값 빈 배열로 지정
  const [list, setList] = useState([]);

// api url json 파일
  const API_URL = 
    "http://makeup-api.herokuapp.com/api/v1/products.json?brand=maybelline";

// axios.get으로 가져오기
    function getData() {
      Axios.get(API_URL).then((res) => {
        console.log(res.data);
        setList(res.data);
      });
    }
// useEffect는 마운트/언마운트/업데이트시 할 작업 설정 할 때 사용
    useEffect(() => {
      getData();
    }, []);
```

```js
// Server Side Rendering 매 요청마다 html을 생성
// - 항상 최신 상태 유지
// getServerSideProps 사용
```

```js
// location and <a> tag makes refresh the page everytime
 location.href = "/about";
 //or
 <a href="/about">about<a>
 ```
```js
  // Link 나 useRouter를 사용하면 refresh 없이 페이지 내부 내용만 변경됨
  <Link/>
  const router = useRouter();
```

## 환경변수 변경

// node.js

process.env.변수명

// browser

process.env.NEXT_PUBLIC_변수명

## error page customizing


### /pages/404.js

```js

import { Icon } from "semantic-ui-react";
// 에러페이지 customizing 하는 페이지 입니다. 
export default function Error404() {
  return (
    <div style={{ padding: "200px 0", textAlign: "center", fontSize: 30 }}>
      <Icon name="warning circle" color="red" />
      404: 페이지를 찾을수 없습니다.
    </div>
  )
}

```

### /pages/_error.js

```js
// basic format
function Error({ statusCode }) {
  return (
    <p>
      {statusCode
        ? `An error ${statusCode} occurred on server`
        : 'An error occurred on client'}
    </p>
  )
}

Error.getInitialProps = ({ res, err }) => {
  const statusCode = res ? res.statusCode : err ? err.statusCode : 404
  return { statusCode }
}

export default Error

```