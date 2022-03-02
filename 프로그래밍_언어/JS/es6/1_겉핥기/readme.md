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

## 1. const, let
- ```const``` : ```var```보다 간력하고 일단 사용되면 변수를 다시 할당할 수 없다.
  - 즉, 객체와 함께 사용할 때를 제외하고는 **변경이 불가능한 함수**.

- const, let를 사용하는 이유는 바로 '호이스팅' 발생을 막는 것이기 때문!이고, 블록 단위의 scope를 사용할 수 있다.
  - hoisting : 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미
    - [호이스팅 참고 자료](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)

- ```var```은 재선언이 가능하다.
- ```let```은 재선언이 불가능하고, 재할당이 가능하다.
- ```const```는 재선언, 재할당이 불가능하다.

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
```javascript
// es5 (old)
function myFunc1() {
    return '안녕' + name + '너의 나이는' + age + '살이다!';
}

console.log(myFunc1('영희', 22));
// 출력 => 안녕 영희 너의 나이는 22살이다!
```

```javascript
// es6
const myFunc = (name, age) => {
    return `안녕 ${name}, 너의 나이는 ${age}살 이다!`;
};

console.log(myFunc1('영희', 22));
// 출력 => 안녕 영희, 너의 나이는 22살 이다!
```

## 4.Default parameters (기본 매개 변수)
- 매개 변수를 쓰지 않은 경우 매개 변수가 이미 기본값에 정의되어 있으므로 정의 되지 않은 오류가 반환되지 않는다.
```javascript
const myFunc = (name, age) => {
    return `안녕 ${name} 너의 나이는 ${age}살 이니?`;
};

console.log(myFunc1('영희'));   // 출력 => 안녕 영희 너의 나이는 undefined살이니?
```
- 위의 함수는 정의되지 않은 상태로 반환된다.
  - 두 번째 매개 변수 ```age```를 지정하는 것을 잊어버렸기 때문이다.

- 그러나 기본 매개 변수를 사용하면 정의되지 않은 매개 변수가 반환되지 않고 매개 변수 할당을 잊어버렸을 때 해당 값이 사용된다.
```javascript
const myFunc = (name, age = 22) => {
    return `안녕 ${name} 너의 나이는 ${age}살 이니?`;
};

console.log(myFunc1('영희'));   // 출력 => 안녕 영희 너의 나이는 22살 이니?
```
- 기본 파라미터를 사용하여 오류를 미리 처리할 수 있다.
## 5. Array and Object destructing (배열 및 객체 비구조화)
- 비구조화를 통해 배열 또는 객체의 값을 새 변수에 더 쉽게 할당할 수 있다.
```javascript
// es5 문법 (old)
const contacts = {
    famillyName: '이',
    name: '영희',
    age: 22
};

let famillyName = contacts.famillyName;
let name = contacts.name;
let myAge = contacts.age;

console.log(famillyName);
console.log(name);
console.log(age);
// 출력
// 이
// 영희
// 22
```

```javascript
// es6+ 문법
const contacts = {
    famillyName: '이',
    name: '영희',
    age: 22
};

let { famillyName, name, age } = contacts;

console.log(famillyName);
console.log(name);
console.log(age);

// 출력
// 이
// 영희
// 22
```
- es5에선 각 변수에 각 값을 할당해야 한다. es6에선 객체의 속성을 얻기 위해 값을 중괄호 안에 넣는다.
- 참고 : 속성 이름과 동일하지 않은 변수를 할당하면 ```undefined```가 반환된다.
  - ex : 속성의 이름이 ```name```이고 ```username``` 변수에 할당하면 ```undefined```를 반환한다.

- 우리는 항상 속성의 이름과 동일하게 변수 이름을 지정해야 한다. 그러나 변수의 이름을 바꾸려면 콜론을 ```:``` 대신 사용할 수 있다.

```javascript
// es6
const contacts = {
    famillyName: '이',
    name: '영희',
    age: 22
};

let { famillyName, name: ontherName, age } = contacts;

console.log(onthername);
// 영희
```

- 배열의 경우 객체와 동일한 구문을 사용한다. 중괄호를 대괄호로 바꾸면 된다.
```javascript
const arr = ['광희', '지수', '영철', 20];

let [value1, value2, value3] = arr;

console.log(value1);
console.log(value2);
console.log(value3);
// 출력
// 광희
// 지수
// 영철
```
## 6. Import and Export
- javascript 응용 프로그램에서 ```import```, ```export```를 사용하면 성능이 향상된다. 이를 통해 별도의 재사용 가능한 구성요소를 작성할 수 있다.


## 7. Promises (프로미스)

## 8. Rest parameter and Spread operator (나머지 매개 변수 및 확산 연산자)

## 9. Classes
