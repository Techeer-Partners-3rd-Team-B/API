# API란?

**서버에서 제공하는 어떤 기능을 Client에서 사용(활용)할 수 있도록 만들어 둔 인터페이스**

🤔 쉽게 말하자면, 클라이언트와 서버 사이를 연결해 주는 매개체라고 할 수 있다.

<aside>
📌 Client ↔ API ↔ Server

</aside>

API는 중간에서 `클라이언트(Client)`의 `요청(Request)`를 받아 서버에게 전달해주고, `서버(Server)`가 요청에 대한 `응답(Response)`을 보내면 그 응답을 클라이언트에게 전달해주는 역할을 한다.

그렇다면 클라이언트와 서버가 API라는 매개체를 통해 통신한다는 것은 알겠는데,

API는 어떤 규칙에 맞게 사용하면 될까?

→ **프로토콜**을 사용해 통신한다

<br/>

## 프로토콜이란?

**서로 다른 통신 장비 간에 데이터를 주고 받을 때 지켜야 하는 규칙** 

<aside>
❗ `API를 사용한다`는 것은 `클라이언트와 서버 간의 통신이 이뤄진다`는 것이기 때문에 통신하기 위한 규칙 즉, `프로토콜`이 필요하다.

</aside>

<br/>
<br/>

# HTTP(Hyper Text Transfer Protocol)란?

**응용 계층의 프로토콜로, 웹에서 통신할 때 가장 흔하게 사용되는 프로토콜이다.**

<br/>

### HTTP에서 요청을 보낼 때 ⇒ `Request message`

Request message는 `start-line`, `Request header`, `Request body`로 구성됨

1. start-line
    
    : HTTP Method, 요청 URL, HTTP의 버전을 담고 있음
    
    ex) `GET /data/2.5/weather? HTTP/1.1`
    

1. Request header
    
    : 요청을 받는 서버의 이름, 서버의 버전, 전달하는 컨텐츠의 타입, 요청 날짜, 요청을 보낸 컴퓨터의 정보 등 다양한 정보를 담고 있음
    
    ex) `Host: api.openweathermap.org`
    
     `User-Agent: Mozilla/5.0`
    
     `Accept-Language: ko-KR`
    
2. Request body
    
    : 서버로 전달하고자 하는 내용이 담김
    
<br/>

### 참고) HTTP Request Method

: GET, HEAD, POST, PUT, DELETE, CONNECT, OPTIONS, TRACE, PATCH

- `GET` : 서버의 데이터를 조회 (Request Body가 없음)
- `POST` : 서버에 데이터를 등록
- `PUT` : 서버의 리소스를 Request body에 담긴 내용으로 수정
- `PATCH` : 서버 리소스의 일부를 수정하는 Method
- `DELETE` : 서버 내 리소스를 삭제하는 Method

<br/>

### HTTP에서 응답을 받을 때 ⇒ `Response message`

Response message는 `status-line`, `Response header`, `Response body`로 구성됨

1. status-line
    
    : HTTP 버전, 상태 코드(Status code), 응답 메시지를 담고 있음
    
    ex) `HTTP/1.1 200 OK`
    
2. Response header
    
    : 응답 날짜, 응답을 전달한 서버의 이름, 서버의 버전, 컨텐츠의 타입 등을 담고 있음
    
3. Response body
    
    : 서버가 클라이언트에게 응답으로 보내는 데이터가 담김
    
<br/>
<br/>

# REST API란?

**REST 아키텍처를 따르는 API** (REST 이외에도 여러 아키텍처를 사용해 API를 설계할 수 있음)

<br/>

### REST(Representational State Transfer)란?

자원(Resource)을 HTTP URI를 통해 명시하고, HTTP Method를 통해 해당 자원에 알맞는 CRUD Operation을 적용한다는 의미 

<br/>

### CRUD Operation이란?

- Create : 생성(POST)
- Read : 조회(GET)
- Update : 수정(PUT)
- Delete : 삭제(DELETE)

<br/>

### REST API 구성 요소

1. 자원(Resource) : URI
    - URI는 자원을 구별하는 고유한 ID를 말함
2. 행위(Verb) : HTTP Method
3. 표현(Representations)
    - 서버에서 클라이언트로 보내는 응답을 말함
    - JSON, XML, TEXT, RSS 등 여러 형태로 나타남
  
<br/>

```jsx
#bad - 행위에 대한 표현이 들어가서는 안됨
GET /getTodos/1
GET /todos/show/1

#good
GET /todos/1
```

```jsx
#bad - URI에는 HTTP 메소드를 사용하지 않음
GET /todos/delete/1

#good
DELETE /todos/1
```
