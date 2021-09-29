# HTTP 메서드 활용
  - 클라이언트에서 서버로 데이터 전송
  - HTTP API 설계 예시  
  
  
  
  ---  
  
### 클라이언트에서 서버로 데이터 전송
 > _데이터 전달 방식은 크게 2가지_
 
 - 쿼리 파라미터를 통한 데이터 전송
   - GET
   - 주로 정렬 필터 (검색어)
     
 - 메시지 바디를 통한 데이터 전송
   - POST, PUT, PATCH
   - 회원 가입, 상품 주문, 리소스 등록, 리소스 변경
     
#### 4가지 상황  
  - __정적 데이터 조회__
    - 이미지, 정적 텍스트 문서
      - 조회는 GET 사용
      - 쿼리 파라미터 없이 리소스 경로로 단순한게 조회 가능  
  - __동적 데이터 조회__
    - 주로 검색, 게시판 목록에서 정렬 필터(검색어)
       - 조회는 GET 사용
       - 쿼리 파라미터 사용
  - __HTML Form을 통한 데이터 전송__
    - 회원 가입, 상품 주문, 데이터 변경
      - `<form action="/save" method ="POST" enctype = "multipart/form-data">`  
      - Content-Type : (default) application/x-www-form-urlencoded 사용
        - form의 내용을 메시지 바디를 통해서 전송 (key-value, 쿼리 파라미터 형식)
        - 전송 데이터를 url encoding 처리 (abc김 -> abc%EA%B9%80)  
      - Content-Type : multipart/form-data
        - 파일 업로드 같은 바이너리 데이터 전송시 사용
        - __다른 종류의 여러파일과 폼의 내용 함께 전송 가능__  
      - &#128293; __HTML Form 전송은 GET, POST만 지원한다!__
  - __HTML API를 통한 데이터 전송__
    - 회원 가입, 상품 주문, 데이터 변경
    - 서버 to 서버
      - backend 시스템 통신
    - 앱 클라이언트
      - ios, android
    - 웹 클라이언트(Ajax)
      - HTML에서 Form 전송 대신 javascript를 통한 통신(Ajax)
      - ex) React, Vue.js 같은 웹 클라이언트와 API 통신
    - POST, PUT, PATCH: 메시지 바디를 통해 데이터 전송
    - GET: 조회, 쿼리 파라미터로 데이터 전달
    - Content-Type: application/json을 주로 사용(default)
      - TEXT, XML, JSON 등
  
  ---  
### HTTP API 설계 예시
  - HTTP API - 컬렉션
    - POST 기반 등록
    - ex. 회원 관리 API 제공
  - HTTP API - 스토어
    - PUT 기반 등록
    - ex. 정적 컨텐츠 관리, 원격 파일 관리
  - HTML FORM 사용
    - 웹 페이지 회원 관리
    - GET, POST만 지원
    
#### API 설계 - POST 기반
  - 회원 목록 /members -> GET
  - 회원 등록 /members -> POST
  - 회원 조회 /members/{id} -> GET
  - 회원 수정 /members/{id} -> &#128161; _PATCH (안전하다)_ , &#128161; _PUT (게시판의 게시글 수정할 때 용이하다)_ , POST
  - 회원 삭제 /members/{id} -> DELETE

#### 회원 관리 시스템
> :star: __POST - 신규 자원 등록 특징__

  - 클라이언트는 등록 될 리소스의 URI를 모른다.
    - 회원 등록 /memebers -> POST
    - POST /members
  - :star: 서버가 새로 등록된 리소스 URI를 생성해준다.
    - __HTTP/1.1 201 Created  
    Location: /members/100__
  - :zap: __Collection__
    - 서버가 관리하는 리소스 디렉토리
    - 서버가 리소스의 URI를 생성하고 관리
    - 여기서 컬렉션은 /memebers
    
#### 파일 관리 시스템
> API 설계 - PUT 기반 등록 (:x: 사용 비중이 적다)
  - 파일 목록 /files -> GET
  - 파일 조회 /files/{filename} -> GET
  - 파일 등록 /files/{filename} -> PUT
  - 파일 삭제 /files/{filename} -> DELETE
  - 파일 대량 등록 /files -> POST
  
> :star: __PUT - 신규 자원 등록 특징__
  - :zap: __클라이언트가 리소스 URI를 알고 있어야 한다.__
    - 파일 등록 /files/{filename} -> PUT
    - PUT /files/star.jpg
  - __클라이언트가 직접 리소스의 URI를 지정한다.__
  - Store
    - 클라이언트가 관리하는 리소스 저장소
    - 클라이언트가 리소스의 URI를 알고 관리
    - 여기서 Store는 /files
    
#### HTML FORM 사용
> HTML FORM은 GET, POST만 지원  
Ajax 같은 기술을 사용해서 해결 가능  
순수 HTML, HTML FORM  
GET, POST만 지원하므로 제약이 있음
>> __컨트롤 URI__
  - 이런 제약을 해결하기 위해 동사로 된 리소스 경로 사용
  - POST의 /new, /edit, /delete가 컨트롤 URI
  - HTTP 메서드로 해결하기 애매한 경우 사용(HTTP API 포함)  
    
- 회원 목록  
  /members -> GET
- 회원 등록 폼  
  /members/new -> GET
- 회원 등록  
  /members/new -> POST
- 회원 조회  
  /members/{id} -> GET
- 회원 수정 폼  
  /members/{id}/edit -> GET
- 회원 수정  
  /members/{id}/edit -> POST
- 회원 삭제  
  /memebers/{id}/delete -> POST


### URI 설계 개념
  - 문서
    - 단일 개념(파일 하나, 객체 인스턴스, 데이터베이스 row)
    - ex. /members/100, /files/star.jpg
  - :star: __컬렉션(Collection)__
    - 서버가 관리하는 리소스 디렉터리
    - 서버가 리소스의 URI를 생성하고 관리
    - /members
  - 스토어(Store)
    - 클라이언트가 관리하는 자원 저장소
    - 클라이언크가 리소스의 URI를 알고 관리
    - /files
  - :star: __컨트롤러(Controller), 컨트롤 URI__
    - 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스 실행
    - 동사를 직접 사용
    - /members/{id}/delete
    
### https://restfulapi.net/resource-naming
