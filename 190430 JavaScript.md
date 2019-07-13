# JavaScript

- 정적이던 문서에 동적인 움직임을 !!

```javascript
alert('Welcome to JS');
```

- 문서에 내용쓰기

```javascript
window.document.write('<h1>Hello world!</h1>');
document.write('<h1 id="hi">Hello world!</h1>');
```

- 새로운 문법

```javascript
let word = "안녕하세요!"
document.write(word)

word = "반갑습니다"
document.write(word)

const word2 = "const안녕하세요!"
document.write(word2)

word2 = "const반갑습니다!"
document.write(word2)
```

- 문자열 이어서 작성가능

```javascript
const firstName = 'happy';
const lastName = 'hacking';
const fullName = firstName + lastName;
document.write('<h1>' + fullName + '!!' + '</h1>');

const firstName = 'happy';
const lastName = 'hacking';
const fullName = firstName + lastName;
document.write(`<h1>${fullName}!!</h1>`);

console.log(`Console ${fullName}`);
```

- input()

```javascript
const userName = prompt('Hello! Who are you?');
let message = `${userName}님 반갑습니다!`

document.write(`<h1>${message}</h1>`)

const userName = prompt("너누구야!!")
if (userName === "admin"){
    document.write("관리자님 안녕하세요!")
} else if (userName === "nawon") {
    document.write("나원님 안녕하세요!")
} else {
    document.write(`${userName}님 안녕하세요!`)
}
```

- 삼항연산자

```javascript
const number = 10
// let result = number === 10 ? true일때 : false일때
number === 10 ? document.write("10은 10이지") : document.write("False")
```

- 0부터 9까지 찍기

```javascript
let i = 0

for (let i=0; i<10; i++) {
    console.log(i)
}
```

- list의 값 찍기

```javascript
let list = [1,2,3,4]
for (let item of list){
    console.log(item)
}
```

- let과 const의 차이점은?

let은 만든 값을 변경 가능하지만 const는 변경 불가능

```javascript
for (const number of [1,2,3,4,5]) {
    console.log(number);
}
```

- 파이썬의 join처럼 합치기 가능 -> 1234

```javascript
let numbers = [1,2,3,4]
q = numbers.join("")
console.log(q)
```

- object는 .으로 찾을수 있음. -> JS Enging 메모리 안에 있는 데이터 구조

```javascript
const me = {
    name:"ssafy",
    PhoneNumber:'01012345678',
    languageLevel:{
        python:'master',
        django:'pro',
        javascript:'junior',
    }
};
console.log(me.languageLevel.django)
```

- JSON은 객체의 내용을 기술하기 위한 text파일

**JSON.stringify()** 메서는 JavaScript 값이나 객체를 JSON 문자열로 변환함.

```javascript
const dessert = {
    coffee : "Americano",
    IceCream : "Sabbaddal",
}
const jsonData = JSON.stringify(dessert);
console.log(jsonData)
console.log(typeof jsonData)
```

`{"coffee":"Americano","IceCream":"Sabbaddal"}                 
string                                                        
`

**JSON.parse()** 메서드는 JSON 문자열의 구문을 분석하고, 그 결과에서 JavaScript 값이나 객체를 생성함.

```javascript
const dessert = {
    coffee : "Americano",
    IceCream : "Sabbaddal",
}
const jsonData = JSON.stringify(dessert);
console.log(jsonData)
console.log(typeof jsonData)

const objectData = JSON.parse(jsonData)
console.log(typeof(objectData))
console.log(objectData)
```

`{"coffee":"Americano","IceCream":"Sabbaddal"}                 
string                                                        
object                                                        
{ coffee: 'Americano', IceCream: 'Sabbaddal' }                `

- 함수

```javascript
const add=function(a,b) {
    return a+b
}

function add(a,b) {
    return a+b
}

const add = (a,b) => {
    return a+b
}

console.log(add(5,10))
```

- 리스트를 받아서 제일 작은 수를 리턴하는 함수

```javascript
const min = (numbers) => {
    let minimum = Infinity
    // 무한대를 나타내는 특수한 값
    for (let number of numbers) {
        if (minimum > number) {
            minimum = number
        }
    }
    return minimum
}

console.log(min([5,6,7,8,9]))
```

- 기본인자함수

```javascript
const sayHello = (name='noName') => {
    console.log(`hi ${name}`)
}

sayHello();
sayHello("나원"); //인자값이 들어가면 hi 나원
```

- 익명함수
  - 1회용으로 사용할 함수는 이름을 짓지 않을 수 있다.(즉시 실행이 필요할 경우 사용)

```javascript
(function () {
    //logic
})();
```

```javascript
(function (num) {console.log(num ** 2)})(5);
((num) => {console.log(num ** 2)})(5);
```

- 배열을 인자로 받아서 그 배열의 모든 수의 합을 리턴

```javascript
const sum = numbers => {
    let sum = 0
    for (const number of numbers){
        sum += number
    }
    return sum
}
sum([1,2,3,4,5])
```

- 배열의 요소들을 각각 [???]한다.

```javascript
// callback으로 변수를 받음.
const numbersEach = (numbers, callback) => {
    let sum
    for (const number of numbers){
        sum = callback(number, sum)
    }
    return sum
}

const addEach = (number, sum=0) => {
    return number + sum
}

console.log(numbersEach([1,2,3], addEach))

```



