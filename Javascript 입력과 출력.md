# Javascript 입력과 출력

### 사용자 입력값 받기 - prompt()

```javascript
// 프롬프트 창이 나타나고 입력값을 확인
prompt()
"오오오오"

// 문장 표시
prompt("이름이 머에요")
"낭니!"

// 디폴트값 같이 설정
prompt("이름이머야?","낭니")
""
```

### 알림 창으로 출력하기 - alert()

```javascript
// 간단한 알림 내용 표시
alert("웰컴!")
undefined
```

### 웹 브라우저 화면에 출력하기 - document.write()

```javascript
var name = prompt("이름: "); // 입력받고

// 괄호 안의 내용을 브라우저 화면에 표시(출력하는 용도)
document.write(name+"님, 어서오세요!"); //출력

undefined //나원님, 어서오세요! 라고 출력됨
```

복습) 나이 출력하기

```javascript
var age = prompt("나이:");
document.write(age+"살 이시군요!");
undefined //25살 이시군요!
```

### 콘솔에 출력하기 - console.log()

```javascript
var name = prompt("이름:");
console.log(name+"님 안녕하세용")
// 나원님 안녕하세용
```

복습) 나이 출력하기

```javascript
var age = prompt("나이:");
console.log(age+"짤입니다!")
// 25짤입니다!
```

