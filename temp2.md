# Android Netword Basic

## 1. 네트워크 통신의 이해

### (1) 네트워크 기본

- 서버와 클라이언트 통신
    - 여기서 '서버'라는 것은 node.js를 뜻하는 것이 아닌, 요청하는 곳의 컴퓨터 자체를 뜻하고, 컴퓨터에는 Node, Mysql, Apache 등
    여러 응용 프로그램이 실행되고 있는 것이다.
    - 클라이언트에서 서버를 찾을 때 사용하는 주소가 IP    
    - IP로 그 서버컴퓨터를 찾아갔다면 그 후 그 안에서 여러 응용프로그램을 찾아가야 하는데, 그 번호가 포트 번호이다. 즉, 데이터베이스에 접속할 것인지 노드에 접속할 것인지를 명시해 주는 것이다. 다만 포트가 없는 것들은 http 프로토콜의 default 포트번호인 80번 포트를 사용한다. 즉, http 로 요청한 후 명시해주지 않으면 http의 포트를 사용하는 것.
    - 소켓 : IP + PORT. 특정 프로그램과 통신하기 위한 숫자를 모아놓은 것이 소켓이다.

- 주소값을 요청 받을 때, 그 이전에 서버를 만들 때 쿼리를 두 가지 형태로 할 수 있다.
    - formUrlEncoded : github.com/json/user
    - 쿼리스트링 : github.com?type=json
- RESTful
    - 현재는 모두 RESTful 방식을 사용하기 때문에 구분할 필요는 없다. RESTful이 나온 이유가 기존 개발자들이 이 방식을 쓰지 않았기
    때문인데, 현재는 모두 사용하기 때문이다.
    - 기존 방식 : http://naver.com/bbs_write.php 처럼 페이지 자체를 호출하고, body 영역에 데이터를 넣어서 보냈다. 각 행동마차
    페이지가 정해져 있어서 각 호출하는 페이지를 바꿔줬다. bbs_write.php, bbs_read.php, bbs_update.php으로 사용됐다.
    - RESTful : 모두 동일한 주소로 호출한다. http://naver.com/bbs로 호출하고 그 대신 주소의 헤더에 메소드를 같이 날려준다. 이게
    원래 웹이 설계된 원리이고, 현재는 모두 이렇게 사용한다. 다만 이게 강제사항이 아니다. 이렇게 쓰자고 하는 방식이다.
    - 쿼리스트링을 사용하는 경우 : 검색은 반드시 쿼리스트링을 사용한다.
    - GET
        - 전체 목록 : http://naver.com/bbs
        - 한 개 값 리턴 : http://naver.com/bbs/3

- json 구조의 이해
    - 객체 지향의 클래스와 정확하게 1대 1로 매핍된다.
    - 3가지 형식의 조합만으로 이루어진다 : 배열 [], 객체 {}, 키 값 
    - 객체 안에 { } 형태로 객체가 들어갈 수 있는데, value : { } 로 사용하거나 { } 로 이름이 없이 사용할 수도 있다
    - value:[{}, {}] 로 배열이 들어갈 수 있다, {}의 이름을 지정하지 않으면 변수명이 value가 되는 것.

## 2. 소켓 통신

## 3. HTTP 통신

### (1) HTTP 메시지/데이터(무엇을 주고받는가)

- HTTP 메시지는 서버와 클라이언트 간에 데이터가 교환되는 방식으로 request는 클라이언트의 요청, response는 그에 대한 서버의 응답

![Request<->Response]()

#### Request 메시지

1. 시작줄
    - POST / HTTP/1.1
    - HTTP 메소드 : GET, HEAD, POST, PUT, DELETE
    - HTTP URL
    - HTTP 버전
2. 헤더
    - Request Header
        - Host : 요청되는 인터넷 호스트와 포트 번호 식별. 포트 번호가 지정되어 있지 않으면 기본 포트 번호 지정
        - User-Agent : 사용자 브라우저의 버전명, OS명, 브라우저 정보Google, Mozilla, FireFox, Safari, IE
        - Accept : 응답하여 해석할 파일의 종류(클라이언트에서 사용할 수 있는 미디어 타입) text/html, application/xml
        - Referer : 호출전 경로
        - Accept-Language : en-us, en;q=0.5
        - Accept-Encoding : 수신 가능한 body 인코딩 종류. 없으면 모든 인코딩 방식을 지원. gzip, deflate는 서버에서 전달되는 데이터가 너무 큰 경우 압축해서 보낼 수 있는데, 문제는 웹브라우저가 압축을 풀 능력이 있는지 알아야 하는 것이다. gzip이나 deflate는 압축을 풀 수 있음을 명시한다. response에 gzip이 있다면 웹서버가 압축해서 보낸 것을 의미한다
        - Accept-Charset : ISO-8859
    - General Header
        - Connection : keep-alive
        - Upgrade-Insecure-Requests : 1
    - Entity Header
        - Content-Type : multipart/form-data
        - Content-Length : 345

![]()


#### Request Data

- POST 방식으로 데이터를 전송할 때에 Request Header를 서버로 전송한 후 Request데이터를 보낸다
- 데이터를 보내는 방식에는 2가지가 있는데 하나는 form-urlencod 를 통해 보내는 방식 또 하나는 multipart-formdata 를 이용해 보내는 방식이 있다. 이 2가지 방식의 차이점은 전자는 일반적인 폼데이터(텍스트위주)만 전송할때 쓰이는 방식이고 아래 방식은 서버로 파일을 전송할때 사용이 된다. 

1. URL Encoded 로 전송
```
Content-Type: application/x-www-form-urlencoded
Content-Length: XX
xxx=XXX&yyy=YYY
```

2. Multi Part Form-data 로 전송 (파일 전송시)
```
Content-Type: multipart/form-data; boundary=--------[boundaryKEY값]
Content-Length: XX 보낼 데이터의 전체적인 길이 

--------[boundaryKEY값]
Content-Disposition: form-data; name="폼이름"; filename="파일이름"
Content-Type: 파일의 MIME 타입

파일 내용

--------[boundaryKEY값]
Content-Disposition: form-data; name="폼이름"

데이터
--------[boundaryKEY값]
```
### (2) HTTP 방법(어떻게 주고받는가)

### (3) HTTP 안드로이드


https://developer.mozilla.org/ko/docs/Web/HTTP/Messages 참고
http://exoluse.egloos.com/v/4572381 참고