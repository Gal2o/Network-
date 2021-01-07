# HTTP 기본
  - 모든 것이 HTTP
  - 클라이언트, 서버 구조 __(Frontend / Backend)__
  - Stateful, Stateless
  - 비 연결성 (Connectionless)
  - HTTP 메시지
  
---

### HTTP (HyperText Transfer Protocol)
#### HTTP 메시지에 모든 것을 전송
  - HTML, TEXT
  - IMAGE, 음성, 영상, 파일
  - JSON, XML (API)
  - _거의 모든 형태의 데이터 전송 가능_
  - __서버 간에 데이터를 주고 받을 때도 대부분 HTTP 사용__  

#### HTTP 역사
  - HTTP/0.9 (1991) : GET 메서드만 지원, HTTP 헤더 X
  - HTTP/1.0 (1996) : 메서드, 헤더 추가
  - HTTP/1.1 (1997) : 가장 많이 사용, 우리에게 가장 중요한 버전
  - HTTP/2 (2015) : 성능 개선
  - HTTP/3 (진행중) : TCP 대신에 UDP 사용, 성능 개선  
  
#### 기반 프로토콜
  - __TCP : HTTP/1.1, 2__
  - __UDP : HTTP/3__
  - 현재 1.1  주로 사용 
    - 2, 3 버전도 점점 사용 증가
      
---  

### Stateful, Stateless
  - Stateful (상태 유지)
  > __중간에 대화하고 있는 사람이 바뀌면 안된다. (바뀔 때, 상태 정보를 미리 알려줘야 함)__  
    __서버에서 상태를 보관한다.__
    
  - __Stateless (무상태)__
    - 서버가 클라이언트의 상태를 보존하지 않음.
    - __클라이언트가 상태를 가지고 서버에 요청__
    - __장점 : 서버 확장성 높음. (스케일 아웃)__
    - _단점 : 클라이언트가 추가 데이터를 전송 해야함._
  > __중간에 대화하고 있는 상대를 마음대로 바꿔도 된다__  
    __응답서버를 쉽게 바꿀 수 있다__  
    __클라이언트 요청이 한번에 증가해도 서버를 대거 투입할 수 있다!__  
    
  - __실무 한계__
    - __모든 것을 무상태로 설계 할 수 있는 경우도 있고 없는 경우도 있다.__
    > Stateful : 로그인 유지  
      Stateless : 로그인이 필요없는 서비스  
    - __되도록이면 Stateless로__
    - __Stateful를 사용해야 한다면, 최소한만 사용 (데이터를 너무 많이 보낸다)__  
---  

### 비 연결성(Connectionless)
  - 연결을 유지 하는 모델 
    - 클라이언트 여러 개가 서버 1개와 연결을 유지 하고 있으면 서버 자원이 계속 낭비  
  - 연결을 유지하지 않는 모델
    - 클러이언트 여러 개와 연결이 필요할 때만 서버의 최소한의 자원만 사용하여 연결함  
> __HTTP는 기본이 연결을 유지하지 않는 모델__  
  일반적으로 초 단위 이하의 빠른 속도로 응답
  1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십 개 이하로 매우 작다.
  서버 자원을 매우 효율적으로 사용할 수 있다.  
  
  - _단점_
    - TCP/IP 연결을 새로 맺어야 함 (TCP 3way handshake 시간 추가)
    - 웹 브라우저로 사이트를 요청할 때마다 HTML, javascript, css 등 수 많은 자원이 다운로드
    
  - __한계와 극복__
    - 지금은 HTTP 지속 연결 (Persitent Connetctions)로 문제 해결
    - HTTP/2, 3 버전 에서 더 많은 최적화가 되었음
     
#### HTTP 지속 연결 
> 클라이언트가 서버에 연결을 요청해서 연결 후, 끊지 않고 지속

## &#9989;최대한 Stateless로 구성하여 많은 트래픽이 와도 무리 없게 만들자!  

---  

### HTTP 메시지
 - HTTP 메시지 구조
   - start-line
     - request-line / status-line
       - request-line : method(_GET, POST, PUT, DELETE_) request-target HTTP-version CRLF
       - status-line : HTTP-version status-code reason-phrase CRLF
   - header
     -header : field-name: field-value
   - empty line (CRLF)
   - message body
     - 실제 전송할 데이터 (HTML, Image, Video, JSON)

