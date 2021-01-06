# URI와 웹 브라우저 요청 흐름  
  
### URI (Uniform Resource Identifier)
  - Uniform : 리소스 식별하는 통일된 방식
  - Resource: 자원, URI로 식별할 수 있는 모든 것
  - Identifier: 다른 항목과 구분하는데 필요한 정보 
> URI? URL? URN?
  
_URI는 로케이터(Locator), 이름(Name) 또는 둘 다 추가로 분류 될 수 있다._
> https://www.ietf.org/rfc/rfc3986.txt
>> URL(Resource Locator) : foo://example.com:8080/over/there?name=?
>>> Locator : 리소스가 있는 위치를 지정  
  
>> URN(Resource Name) :  example:animal:ferret:nose (그냥 이런게 있다 정도만 알면 된다.)  
>>> Name: 리소스엠 이름을 부여

  - URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않음
  - __앞으로 URI를 URL과 같은 의미로 칭하자__
  
#### 전체 문법  
  - scheme://[userinfo@]host[:port][/path][?query][#fragment]
  - http:s//google.com:443/search?q=hello  
    
  - 프로토콜 (https)
  - 호스트명 (www.google.com)
  - 포트 번호 (443) (_생략_)
  - 패스 (/sesarch) (계층적 구조)
  - 쿼리 파라미터(?q=hello) (key-value 형태)
  - fragment (html 내부 북마크 등에 사용, 서버에 전송하는 정보는 아니다.)
  
  ---  
  
  ### 웹 브라우저 요청 흐름  
  #### http:s//google.com:443/search?q=hello  
  
  1. 웹 브라우저가 DNS서버를 조회 해서 google.com의 IP주소, Port주소를 찾고 HTTP 요청 메세지를 생성
  > GET /search?q=hello HTTP/1.1 Host:wwww.google.com
  2. SOCKET 라이브러리를 통해 전달 
    - A: TCP/IP 연결
    - B: 데이터 전달
  3. TCP/IP 패킷 생성, HTTP 메시지 포함
  4. 요청 패킷 도착 -> 패킷을 분석 -> HTTP 응답 메세지 생성
  > HTTP/1.1 200 OK  
  > Content-Type: text/html;charset=UTF-8
  5. 응답 데이터 분석 -> 웹 브라우저 HTML 렌더링
