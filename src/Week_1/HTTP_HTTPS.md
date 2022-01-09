### HTTP 와 HTTPS 의 차이점

#### 답변

* HTTP는 이전 GET 과 POST를 공부하기위해 어느정도 알아보았다.
* 이제는 HTTP와 HTTPS 가 어떤 차이가 있는지 더 구체적으로 알아보기위해 구글링을 하였다.  

[HTTP HTTPS](https://velog.io/@sdc337dc/%EC%9B%B9-%EA%B0%9C%EB%85%90-Http-%ED%86%B5%EC%8B%A0)  

* 우선 HTTP 와 HTTPS 를 알기전에 웹 통신에대해 공부를 해보아야 될것 같았다.

##웹 통신

### 웹통신 & Protocol
- 인터넷 상에서의 통신을 의미.  
  

- 인터넷에서의 엄격한 규약 = Protocol

### Protocol 종류

- 일반적인 프로토콜
  - Http : Hyper Text Transfer Protocol
  - Https : Hyper Text Transfer Protocol Secure  
    

- TCP/IP 프로토콜을 가지고 서버와 클라이언트 사이의 파일 전송을 하기위한 프로토콜  
  - FTP : File Transfer Protocol  
    

- 파일 전송 프로토콜
  - Telnet : Terminal Network
  - SSH : Secure Shell  
    
    
- 보안된 소켓통신을 위한 프로토콜
  - SMTP : Simple Mail Transfer Protocol  
    

- 기타 
  - TCP/UDP : Transmission Control Protocol/User Datagram Protocol
  - IP : Internet Protocol  

    
    
### HTTP 프로토콜

- Hyper Text( 웹문서를 구성하고 있는 언어 = HTML) 를 전송하기위한 프로토콜 (80번 포트 사용)  

    
- HTML : 웹 문서의 뼈대를 구성하는 언어. 브라우저를 통해서 웹 문서를 읽을 수 있다.  
  - Hyper Text Markup Language  
  - Hyper Text : Text를 넘어서 링크, 이미지 등 다양한 것들을 표현할 수 있는것.  

  
- HTTP 통신 (Request & Response)
  - Request , Response 로 이루어짐  
  - 클라이언트가 서버에게 요청을 보냄
  - 서버는 요청에대한 응답 결과를 줌
  - 클라이언트 사용자에게 응답 받은 결과를 보여줌    
  
  
- Request / Response 구조  

![이미지](https://media.vlpt.us/images/sdc337dc/post/83c5250a-805e-4c2f-ac94-c221bb97ecba/image.png)


- HTTP 통신 (Stateless)   
  - HTTP 통신은 State 개념이 존재하지 않는다.
  - 통신을 주고 받아도 클라이언트와 서버는 연결되어있는 것이 아니라 각각이 독립적인것이다.
  - 상태를 저장하지 않는다는 의미이다. 
  - 로그인 같은 경우 세션/저장소 같은 방식으로 이용해 기억하는거처럼 보이게 한다.  
    
    
- HTTP 패킷
  - HTTP 통신은 요청을 보내고 응답을 받을때 그 정보들을 패킷에 넣어 보낸다.
  - 패킷 구조 : Header + Body
     - Header : 보내는 사람의 주소, 받는사람의 주소, 패킷 생명시간
     - Body : 실제 전달하고자 하는 내용  
      

  - 요청과 응답에 담겨있는 정보 
    ![이미지](https://media.vlpt.us/images/sdc337dc/post/19c3100a-bfba-4fb3-bce9-9b0d702a2f50/image.png)
  - General : 요청 url 정보와 메소드, 상태코드를 확인할 수 있다.
  - Response Headers : 응답헤더 : 응답 온 패킷의 헤더를 확인할 수 있다. 서버의 종류,연결상태 등등
  - Request Headers : 요청헤더 : 요청을 보낸 패킷의 헤더를 확인할 수 있다. 보낸 클라이언트의 종류, 요청한 파일의 종류 등등
    
- HTTP Request 구조
  - Start Line(요청내용)
  - Header
  - Body  
    
- HTTP Request 구조 - Http 메소드
  - GET : URL이 가진 정보를 검색하기 위해 서버측에 요청하는 형태이다.
     - 전송방식 : GET [request-uri]?query_string  
       Host:[Hostname] 혹은 [IP] \r\n  
       
    
  - POST : URL에 폼 입력을 처리하기 위해 구성한 서버 측 스크립트(ASP, PHP, JSP 등) 혹은 CGI프로그램으로 구성되고 Form Action과 함께 전송되는데, 이때 헤더 정보에 포함되지않고 데이터 부분에 요청 정보가 들어가게된다.  
    

  - PUT : POST와 유사한 전송구조를 가지기 때문에 헤더 이외에 메세지가 함께 전송된다.  
    

  - DELETE : 원격지 웹 서버에 파일을 삭제하기위해 사용되며 PUT과는 반대개념의 메소드  

- HTTP Response 구조 - 응답코드 종류
![이미지](https://media.vlpt.us/images/sdc337dc/post/a8ea6cea-d678-4a0f-a1c5-f661b169f245/image.png)
  
### HTTPS 프로토콜

- HTTPS 프로토콜은 SSL 프로토콜을 덮어쓴 HTTP 라 할 수 있다. (443번 포트 사용)
- 통신하는 소켓부분을 SSL로 대체한다. TCP와 직접 통신하는것이 아니라 SSL을 한번 거쳐서 통신하기에 보안이나 안정성에서 업그레이드 된다.  

- 공개키 암호화 방식을 사용하여 CA에 공개키를 전송하여 인증서를 발급받아 클라이언트에게 공개키와 함께 제공한다. (신뢰할 수 있는 사이트라고 확인)
- 검색엔진에서 사용자가 키워드를 검색시 상위노출 기준중 하나가 보안이기때문에 HTTP보다 상위 노출 가능성 높음.

- 브라우저가 서버에 접속시 서버는 CA로부터 받은 인증서를 제공 (공개키 포함)
- 브라우저는 CA리스트를 가지고 있는데 그 리스트에 CA인증서가 리스트에 있는 CA인지 확인 후 인증서의 서비스 정보를 공개키로 복호화
- 이제 통신에 사용할 대칭키를 공개키로 암호화하여 보낸걸 서버가 복호화 후 대칭키를 얻어 서로 대칭키로 통신
