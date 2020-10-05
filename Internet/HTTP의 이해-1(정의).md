# HTTP (Hyper Text Transfer Protocol)

**인터넷에서 서버와 클라이언트 간의 데이터를 주고 받을 수 있도록 하는 프로토콜(상호 간에 정의한 규약)** 입니다.


## HTTP 프로토콜 특징

**상태가 없는 (stateless) 프로토콜**입니다. 여기서 상태가 없다라는 말은 각각의 데이터 요청이 서로 독립적이므로 관련이 없다는 말입니다.

이러한 특징으로 다수의 요청 처리 및 서버 부하를 줄일 수 있는 성능 상의 이점이 생기기도 하지만, 반대로 독립적이라는 단점을 해결하기 위해 `Cookie` 나 `Session` 이 등장하였습니다.

또한 HTTP 프로토콜은 일반적으로 [TCP/IP 통신](https://brunch.co.kr/@wangho/6) 위에서 동작합니다.   


## HTTP Request & HTTP Response

HTTP 프로토콜로 데이터를 주고받기 위해서는 아래와 같이 클라이언트에서 요청(Request) 를 보내고 서버에서 응답(Response)를 받아야 합니다.

![Alt text](https://joshua1988.github.io/images/posts/web/http/request-response.png)

클라이언트란 요청을 보내는 쪽을 의미하며 일반적으로 웹 관점에서는 브라우저를 의미합니다. 서버란 요청을 받는 쪽을 의미하며 일반적으로 데이터를 보내주는 원격지의 컴퓨터를 의미합니다.   

HTML 문서만이 HTTP 통신을 위한 유일한 정보는 아닙니다. Plain Text 부터 JSON 데이터 및 XML 과 같은 형태의 정보도 주고 받을 수 있습니다.

## URL

숫자로 된 IP 주소를 대체하는 **도메인 네임 시스템**입니다. URL(또는 URI) 라는 단어 자체는 네트워크 상에서 주소를 나타내기 위한 정식적인 규약 명칭입니다.

![Alt text](https://joshua1988.github.io/images/posts/web/http/url-structure.png)

위 URL 구조를 구분지어 살펴보겠습니다.

### Protocol

프로토콜은 해당 URL 이 어떤 서비스를 위한 것인지 명시합니다. http 및 https는 웹 서비스를 위한 프로토콜, ftp는 파일 서버가 사용하는 프로토콜을, ssh는 리눅스 기반 통신 프로토콜입니다.

### 최상위 도메인(TLD, Top Level Domain)

최상위 도메인은 com, net, kr 처럼 도메인 주소의 끝에 붙는 녀석입니다. 

### 서브 도메인(Sub-domain)

도메인 주소의 오른쪽에 있는 TLD 부터 점을 구분하여 나열되는 각 문자들을 **서브 도메인**이라 합니다. naver.com 에서 naver 가 서브 도메인이 되는데, 일반적으로 우리가 도메인을 구입하면 example.com 형식으로 할당받기 때문에 example 이나 naver 처럼 TLD 바로 옆에 있는 도메인은 주로 **메인 도메인**이라고 부릅니다. 메인 도메인 왼쪽부터 서브 도메인이라 칭하는 것이 일반적입니다.


## HTTP 요청 메서드

URL(Uniform Resource Locators) 주소를 이용하면 서버에 특정 데이터를 요청할 수 있습니다. 아래와 같은 HTTP 요청 메서드(HTTP Request Methods)를 이용합니다.

- **GET** : 존재하는 자원에 대한 **요청**
- **POST**: 새로운 자원을 **생성**
- **PUT**: 존재하는 자원에 대한 **변경**
- **DELETE**: 존재하는 자원을 **삭제**

이와 같이 데이터에 대한 조회, 생성, 변경, 삭제를 HTTP 요청 메서드로 정의할 수 있으며, 때에 따라서는 POST 로 PUT, DELETE 의 동작도 수행할 수 있습니다.


## HTTP 상태 코드

URL 과 요청 메서드가 클라이언트에서 설정해야 할 정보라면 HTTP 상태 코드(HTTP Status Code) 는 서버에서 설정해주는 응답(Response) 정보입니다.

서버로부터 받는 이 상태 코드를 이용하여 프론트엔드에서 에러 처리를 할 수 있습니다.

### 2xx - 성공

200번대의 상태 코드는 대부분 성공을 의미합니다.

* 200 : GET 요청에 대한 성공
* 204 : No Content. 성공했으나 응답 본문에 데이터가 없음
* 205 : Reset Content. 성공했으나 클라이언트의 화면을 새로 고침하도록 권고
* 206 : Partial Content. 성공했으나 일부 범위의 데이터만 반환

### 3xx - 리다이렉션

300번대의 상태 코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL 로 리다이렉트를 유도하는 경우입니다.

* 301 : Moved Permanently, 요청한 자원이 새 URL에 존재
* 303 : See Other, 요청한 자원이 임시 주소에 존재
* 304 : Not Modified, 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐싱된 자원을 사용하도록 권고. ETag와 같은 정보를 활용하여 변경 여부를 확인

### 4xx - 클라이언트 에러

400번대 상태 코드는 대부분 클라이언트의 코드가 잘못된 경우입니다. 유효하지 않은 자원을 요청했거나, 요청이나 권한이 잘못된 경우에 발생합니다. 가장 익숙한 코드는 요청한 자원이 서버에 없다는 의미를 가지는 404 상태 코드입니다.

* 400 : Bad Request, 잘못된 요청
* 401 : Unauthorized, 권한 없이 요청. Authorization 헤더가 잘못된 경우
* 403 : Forbidden, 서버에서 해당 자원에 대해 접근 금지
* 405 : Method Not Allowed, 허용되지 않은 요청 메서드
* 409 : Conflict, 최신 자원이 아닌데 업데이트 하는 경우. ex) 파일 업로드 시 버전 충돌

### 5xx - 서버 에러

500번대 상태 코드는 서버 쪽에서 오류가 난 경우입니다.

* 501 : Not Implemented, 요청한 동작에 대해 서버가 수행할 수 없는 경우
* 503 : Service Unavailable, 서버가 과부하 또는 유지 보수로 내려간 경우


## 다시 살펴보는 HTTP 요청과 응답

앞에서 배운 URL, 요청 메서드, 상태 코드를 조합하면 아래와 같은 구조가 나옵니다.

![Alt text](https://joshua1988.github.io/images/posts/web/http/http-full-structure.png)
