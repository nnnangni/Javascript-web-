# 190502 - JavaScipt 배열 메소드

### forEach 

-> 리턴이 없음

```javascript
const colors = ["red", "green", "yellow"]

for (const color of colors){
    console.log(color)
}

// colors.forEach(()=>{})
colors.forEach(function(color){
    console.log(color)
})
```

- 연습하기

```javascript
function handlePosts(){
    const posts = [
        {id:1, title:"hihi"},
        {id:13, title:"hello"},
        {id:17, title:"123123"},
    ]

    // for (let i=0; i<posts.length; i++){
    //     console.log(posts[i].title)
    // }

    // 위의 코드를 forEach로 실행
    posts.forEach(function(post){
        console.log(post.title)
    })
}
handlePosts()
```

- 만약 인덱스만 출력하고싶다면?

```javascript
function handlePosts(){
    const posts = [
        {id:1, title:"hihi"},
        {id:13, title:"hello"},
        {id:17, title:"123123"},
    ]
	
    // 인자에 인덱스 같이 넣어주기
    posts.forEach(function(post, index){
        console.log(index)
    })
}
handlePosts()
```

- q는????????

```javascript
function handlePosts(){
    const posts = [
        {id:1, title:"hihi"},
        {id:13, title:"hello"},
        {id:17, title:"123123"},
    ]
	
    // q는 전체 posts 자체를 호출한다.
    posts.forEach(function(post, index, q){
        console.log(q)
    })
}
handlePosts()
```

결과값

```bash
student@DESKTOP MINGW64 ~/Desktop/js
$ node arrayHelper.js
[ { id: 1, title: 'hihi' },
  { id: 13, title: 'hello' },
  { id: 17, title: '123123' } ]
[ { id: 1, title: 'hihi' },
  { id: 13, title: 'hello' },
  { id: 17, title: '123123' } ]
[ { id: 1, title: 'hihi' },
  { id: 13, title: 'hello' },
  { id: 17, title: '123123' } ]
```

map 

##### 하나하나 연산하고 연산에 대한 결과를 return

```javascript
const numbers = [1,2,3]

// numbers.map은 위에 1,2,3 을 하나씩 찾아감.
const double = numbers.map(function(number){
    // 동작을 실행한 후 새로운 배열 double에 들어감.
    return number * 2
})
console.log(double)
```

- map 연습문제

```javascript
const images = [
    {h:"30px", w:"30px"},
    {h:"50px", w:"500px"},
    {h:"100px", w:"1000px"},
]

// map을 사용하여 const h = ["30px","50px","100px"] 이라는 결과가 나오도록

const h = images.map(function(image){
    return image.h
})
console.log(h)

const trips = [
    {distance:30, time:10},
    {distance:90, time:50},
    {distance:59, time:25},
]

// 속도값이 들어있는 배열을 반환

const speed = trips.map(function(trip){
    return trip.distance/trip.time
})
console.log(speed)
```

### filter

```javascript
const products = [
    {name:"phone", value:100},
    {name:"notebook", value:200},
    {name:"desktop", value:200},
    {name:"mouse", value:1},
]

// value가 200인 항목만 가져와서 새로운 배열 만들기
const twoH = products.filter(function(product){
    return product.value === 200
})
console.log(twoH)
```

- 함수를 인자로 넣기

```javascript
const numbers = [10,20,30]

// callback 함수 사용하기
function reject(array, iterate){
    // 여기에 코드작성
    // return array.filter(function(item){
    //     return item < 15
    // })
    return array.filter(function(item){
        return iterate(item)
    })
}

// reject라는 함수에 numbers와 function(number){return number < 15}를 인자로 넣음
const lessThan15 = reject(numbers, function(number){
    return number < 15
})

console.log(lessThan15)
```

- 만약 반대의 경우?

```javascript
const numbers = [10,20,30]

function reject(array, iterate){
    // 여기에 코드작성
    return array.filter(function(item){
        // 느낌표는 true는 false, false는 true를 반환해준다.
        return !iterate(item)
    })
}

const lessThan15 = reject(numbers, function(number){
    return number > 15
})

console.log(lessThan15)
```

- 그대로 함수를 넣어줘도 가능

```javascript
const numbers = [10,20,30]

function reject(array, iterate){
    // 여기에 코드작성
    return array.filter(iterate)
}

const lessThan15 = reject(numbers, function(number){
    return number < 15
})

console.log(lessThan15)
```

### find

find는 하나를 찾으면 그 다음배열의 요소에는 접근하지 않음.

```javascript
const heros = [
    {name:'iron man'},
    {name:'thor'},
    {name:'captain'}
]

const tony = heros.find(function(hero){
    return hero.name == "iron man"
})

console.log(tony)
```

