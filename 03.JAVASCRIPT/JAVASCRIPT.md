# Javascript 관련
## toString() / toLocaleString()

```js
toString() // 문자열 반환
toLocaleString() // 문자열 반환 및 ,(쉼표)로 구분지어줌
```

## concat()

```js
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
// 배열 array1과 array2 배열을 합쳐줌
```

## some()

- 배열안에 배열에 대해 조건 부여(i > 0) 및 값 비교등 하려면
- some()은 배열의 각 엘리먼트에 대해서 테스트 함수의 반환 값이 하나라도 true가 있는지 확인합니다.
- 하나라도 true가 발생하면 true를 반환합니다.
- 모두 false인 경우만 false를 반환합니다.
- every가 and 조건이라면 some은 or 조건입니다.
- 기존 배열 값은 변경되지 않습니다.

```js
// arr.some(function(currentValue, index, array), thisValue))
// objArr = [{name: '철수', age: 10},{name: '영희', age: 10}, {name: '바둑이', age: 2}]
// console.log(objArr.some((item)=> item.age>5)); //true
// console.log(objArr.some((item)=> item.age>10)); //false (모두 탈락!)
const check = list.map((li) => li.files)
<View>
  {check.some((c) => c > 0) && (<Text>0보다 큽니다</Text>)} 
</View>
// 배열 안에 있는 값들에 대해 0보다 큰 경우
```
