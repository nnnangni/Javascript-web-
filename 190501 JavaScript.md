# 190501 JavaScript

- 버튼달아주기

```html
    <div id="me"></div>
    <button id="my-btn">click</button>
    <script>
        /* 
            [무엇]을 [언제] [어떻게] 한다.
            버튼을    클릭하면  뿅 한다.
        */
       // 1. 무엇 => 버튼
       const button = document.querySelector('#my-btn')
       console.log(button)
    </script>
```

- 클릭이라는 이벤트가 들어오면 callback함수를 실행해!

```html
       // 2. 언제 => 버튼을 '클릭' 하면
       button.addEventListener('click', what)
```

- 함수실행

```html
       // 3. 어떻게 => 뿅 이라는 단어를 쓴다. (함수만들어서 사용)
       const what = (e) => {
           const area = document.querySelector("#me")
           area.innerHTML = "<h1>뿅</h1>"
       }
```

- () => {}

  : 함수구조와 같아 fuction으로 쓸 수 있음 => function(){}

- 익명함수를 사용한다면?

```html
    <div id="me"></div>
    <button id="my-btn">click</button>
    <script>
        /* 
            [무엇]을 [언제] [어떻게] 한다.
            버튼을    클릭하면  뿅 한다.
        */
       // 1. 무엇 => 버튼
       const button = document.querySelector('#my-btn')
       console.log(button)

       // 3. 어떻게 => 뿅 이라는 단어를 쓴다. (함수만들어서 사용)
    //    const what = (e) => {
    //        const area = document.querySelector("#me")
    //        area.innerHTML = "<h1>뿅</h1>"
    //        console.log(e)
    //    }

       // 2. 언제 => 버튼을 '클릭' 하면
       // event는 함수호출인자, event부터 console.log까지는 하나의 함수
       button.addEventListener('click', (event) => {
           const area = document.querySelector("#me")
           area.innerHTML = "<h1>뿅</h1>"
           console.log(event)
       })
    </script>
```

- 버튼을 클릭하면 글자색 바꾸기 (중요중요)

```html
    <h1 id="hello">안녕하세요</h1>
    <button id="hello-btn">얍!!!</button>
       // 1. 무엇 => 얍버튼
       const button2 = document.querySelector('#hello-btn')
       // 2. 언제 => '클릭'하면
       button2.addEventListener('click', (event2) => {
           // 3. 어떻게 => 안녕하세요라는 단어의 색깔을 바꾼다.
            const hello = document.querySelector("#hello")
            hello.style.color = "blue"
            console.log(event2)
       })
```

### 공룡 움직이기

- dino.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .bg {
            background-color: #F7F7F7;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
    </style>
</head>
<body>
    <div class="bg">
        <img id="dino" width="100px" heigth="100px" src="https://is4-ssl.mzstatic.com/image/thumb/Purple118/v4/88/e5/36/88e536d4-8a08-7c3b-ad29-c4e5dabc9f45/AppIcon-1x_U007emarketing-sRGB-85-220-0-6.png/246x0w.jpg" alt="dino">
    </div>

    <script>
        const dino = document.querySelector("#dino")
        dino.addEventListener('click', (e)=>{
            console.log("아야")
        })
        // 키가 눌리길 기다림
        let x = 0;
        let y = 0;

        document.addEventListener('keydown', e => {
            if (e.key==="ArrowLeft") {
                console.log("왼")
                x += 20
                dino.style.marginRight = `${x}px`
            } 
            else if (e.key==="ArrowRight"){
                console.log("오")
                x -= 20
                dino.style.marginRight = `${x}px`
            }
            else if (e.key==="ArrowUp"){
                console.log("위")
                y -= 20
                dino.style.marginTop = `${y}px`
            }
            else if (e.key==="ArrowDown"){
                console.log("아래")
                y += 20
                dino.style.marginTop = `${y}px`
            }
            else {
                console.log(`${e.key}버튼`)
            }
            // console.log(e)
        })
    </script>
</body>
</html>
```

### webAPI

- GET방식으로 보내기

```javascript
    <script>
        const URL = "https://jsonplaceholder.typicode.com/posts"    
        const XHR = new XMLHttpRequest()
        XHR.open('GET', URL)
        XHR.send()
        XHR.addEventListener('load', function(e){
            const result = e.target.response
            // console.log(result)
            const parseData = JSON.parse(result)
            console.log(parseData)
        })

    </script>
```

- POST방식으로 보내기

```javascript
    <script>
        const URL = "https://jsonplaceholder.typicode.com/posts"    
        const XHR = new XMLHttpRequest()
        XHR.open('POST', URL)
        XHR.setRequestHeader(
            'Content-Type', 'application/json;charset=UTF-8'
        )
        const data = {
            title:"안녕하세요",
            body:"곧 점심",
            userId:1
        }
        const jsonData = JSON.stringify(data)
        XHR.send(jsonData)
        XHR.addEventListener('load', function(e){
            const result = e.target.response
            // console.log(result)
            const parseData = JSON.parse(result)
            console.log(parseData)
        })

    </script>
```

- axios

```javascript
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
    <script>
        const URL = "https://jsonplaceholder.typicode.com/posts"
        // axios.get(URL).then((response) => console.log(response.data))
        const body = {
            title:"new post",
            body:"texttexttext",
            userId:1
        }
        axios.post(URL, body).then(response => console.log(response.data)) 
    </script>
```

- 좋아요 취소

```html
    <!--자바스크립트 쿼리셀렉터올을 통해 like-btn을 가지고있는 모든 쿼리를 가져옴-->
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
    <script type="text/javascript">
        let likeBtnList = document.querySelectorAll('.like-btn')
        console.log(likeBtnList)
        
        // 필요한 정보만 가져오기위해
        for(const likeBtn of likeBtnList){
            // console.log(likeBtn) //각각의 요소 하나하나 뽑기
            likeBtn.addEventListener('click',(e)=>{
                console.log(e.target) //내가 무엇을 클릭했나 확인
                const post_id = e.target.dataset.id
                axios.get(`/posts/${post_id}/like/`)
                .then(function(response){
                    // 좋아요가 눌렸다
                    if (response.data.is_like){
                        e.target.classList.remove('far')
                        e.target.classList.add('fas')
                        e.target.style.color = "#ed4956"
                    // 좋아요가 취소됐다
                    } else {
                        e.target.classList.remove('fas')
                        e.target.classList.add('far')
                        e.target.style.color = "black"
                    }
                })
                .catch(function(error){
                    console.log(error)
                })
            })
        }
    </script>
```

- views.py

```python
@login_required        
def like(request, id):
    user = request.user
    post = Post.objects.get(id=id)
    
    # 사용자가 좋아요를 눌렀다면
    if user in post.likes.all():
        post.likes.remove(user)
        is_like = False
    # 사용자가 좋아요를 누르지 않았다면
    else:
        post.likes.add(user)
        is_like = True
    
    return JsonResponse({"is_like":is_like, "like_count":post.likes.count})
```

