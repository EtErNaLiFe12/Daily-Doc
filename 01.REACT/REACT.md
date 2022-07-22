## React start
npx create-react-app my-app

## material ui

https://mui.com/
https://goo-gy.github.io/2021-02-28-material-ui

npm install @material-ui/core
npm install @material-ui/icons


## react slick - css customizing

```tsx
const settings = {
  dots: true,
  arrows: true,
  autoplay: true,
  slidesToShow: 1,
  slidesToScroll: 1,
  infinite: true,
  speed: 1000,
  appendDots: (dots: any) => {
    return (
      <Box
        component="li"
        sx={{
          position: 'absolute',
          top: 2,
          right: 20,
          '&.slick-dots': {
            textAlign: 'right'
          },
          '&.slick-dots li button:before': {
            color: '#fff !important'
          }
        }}
      >
        {dots}
      </Box>
    );
  }
};
```

## react-lottie animation

### package install
yarn add react-lottie
yarn add @types/react-lottie

```tsx

import Lottie from 'react-lottie';
import animationData from 'assets/hi.json';

  const defaultOptions = {
    loop: true,
    autoplay: true,
    animationData: animationData,
    rendererSettings: {
      preserveAspectRatio: 'xMidYMid slice'
    }
  };

 <Lottie options={defaultOptions} height={400} width={300} />
```

## Scroll action(as like toss)

```js
  window.scrollTo({
    top: scroll.current?.offsetTop! - 60,
    behavior: 'smooth'
  });
```


## useSelector 최적화

```js
import { shallowEqual } from 'react-redux';

function CounterContainer() {
  const { number, diff } = useSelector(
    state => ({
    number: state.counter.number,
    diff: state.counter.diff
  }),
  shallowEqual
  );
}

```

## animation style css 

```jsx
 sx={{
    height: 28,
    borderRadius: 14,
    [`&.${linearProgressClasses.colorPrimary}`]: {
      backgroundColor: COLORS.chartGray
    },
    [`& .${linearProgressClasses.bar}`]: {
      borderRadius: 14,
      backgroundColor: COLORS.primary400,
      animation: 'linear-translate 1s linear',
      '@keyframes linear-translate': {
        from: {
          transform: 'translateX(-100%)'
        }
      }
    }
  }}
```