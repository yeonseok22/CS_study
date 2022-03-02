# 겉핥기

- [참조한 자료 홈페이지 1](https://velog.io/@kimhscom/JavaScript-%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-ES6-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%A6%AC)
- [참조한 자료 홈페이지 2](https://velog.io/@hyeonyohwan/JavaScript-ES6-%EB%AC%B8%EB%B2%95)
# intro
- ES6은 다음과 같은 기능을 포함하고 있다.
  - const, let
  - Arrow Function (화살표 함수)
  - Template Literals (템플릿 리터럴)
  - Default parameters (기본 매개 변수)
  - Array and Object destructing (배열 및 객체 비구조화)
  - Import and Export
  - Promises (프로미스)
  - Rest parameter and Spread operator (나머지 매개 변수 및 확산 연산자)
  - Classes
  - Destructuring

## 1. const, let
- ```const``` : ```var```보다 간력하고 일단 사용되면 변수를 다시 할당할 수 없다.
  - 즉, 객체와 함께 사용할 때를 제외하고는 **변경이 불가능한 함수**.

- 기존에는 ```var```를 사용했는데, ```var```는 '호이스팅(hoisting)'이기 때문에 변수를 재할당하지 않으려면 항상 상수, ```const```를 사용하는 것이 좋다.
  ```javascript
  // ES5 (old)
  var MyBtn = document.getElementById('mybtn');
  
  // ES6
  const MyBtn = document.getElementById('mybtn');
  ```
  
  - 위의 코드에선, ```const```는 변경되지 않으며 재할당할 수 없다. 새로운 값을 제공하려고 하면 오류가 반환된다.

- ```let```은 새로운 값을 가질 수도 있고 재할당할 수도 있다. 변경 가능한 변수가 생성된다.
  ```javascript
  let name = '철수';
  
  name = '영희';
  
  console.log(name);    // 출력 => 영희
  ```
  
  - ```let```은 ```const```와 동일하게 모두 블럭 범위라는 점이다.
    - 즉, 변수는 범위 내에서만 사용할 수 있다.


## 2. Arrow Function (화살표 함수)
- 더 가독성 있게, 더 체계적이게, 새삥나게 보임
```javascript
// es5 (old)
function myFunc(name) {
    return '안녕' + name;
}

console.log(myFunc('영희'));

// 출력 => 안녕 영희

// es6+ 화살표 함수
const myFunc = (name) => {
    return '안녕 &{name}';
}

console.log(myFunc('영희'));    // 출력 -> 안녕 영희

// es6+ 화살표 함수 더 멋지게
const myFunc = (name) => '안녕 ${name}';
console.log(myFunc('영희'));    // 출력 -> 안녕 영희

// 더욱 깔끔하게 보임!!
```

- 또한, 화살표 함수를 ```map```, ```filter```, ```reduce`` 등 내장 함수와 함께 사용할 수 있다.
```javascript
// es5 (old)
const myArray = ['진수', '영철', '영희', 5];

let arr1 = myArray.map(function(item) {
    return item;
});

console.log(arr1);    // 출력 => (4) ["진수", "영철", "영희", 5]

// es6
let arr2 = myArray.map((item) => item);

console.log(arr2);    // 출력 => (4) ["진수", "영철", "영희", 5]
```
- 이렇듯, ES6의 화살표 함수를 사용하면 더 스마트한 코드를 작성할 수 있다.
  - ```filter```와 ```reduce```같은 동일한 함수를 사용할 수 있다.

## 3. Template Literals (템플릿 리터럴)
- 문자열을 연결하기 위해 더하기(```+```) 연산자를 사용할 필요는 없으며, 백틱을 사용하여 문자열 내에서 변수를 사용할 수도 있다.


## 4.Default parameters (기본 매개 변수)

## 5. Array and Object destructing (배열 및 객체 비구조화)

## 6. Import and Export

## 7. Promises (프로미스)

## 8. Rest parameter and Spread operator (나머지 매개 변수 및 확산 연산자)

## 9. Classes
 
## 10. Destructuring
