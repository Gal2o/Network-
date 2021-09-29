### HTTP 헤더 
  - header-field = field-name ":" OWS field-value OWS (OWS: 띄어쓰기 허용)
  - field-name은 대소문자 구분 없음
  
> 용도
  - HTTP 전송에 필요한 모든 부가 정보
  - 메시지 바디 내용, 크기, 압축 등등..
  - 표준 헤더가 너무 많음
  - 필요시 임의의 헤더 추가 가능 
  
### HTTP 표준 (RFC 7230 ~ 7235)
  - 메시지 바디를 통해 표현 데이터 전달 
  - 메시지 바디 = 페이로드
  - __표현은__ 요청이나 응답에서 전달할 실제 데이터
    - _왜 표현인가? 요청에 응답하는 데이터를 JSON으로 리턴 할 수도 있고, HTML로 리턴 할 수도 있다. => 표현_
  - __표현 헤더는 표현 데이터를__ 해석할 수 있는 정보 제공
    - 데이터 유형(HTML, JSON), 데이터 길이, 압축 정보 등등
  
### 표현  
  - Content-Type : 표현 데이터의 형식
  - Content_Encoding : 표현 데이터의 압축 방식
  - Content-Language : 표현 데이터의 자연 언어
  - Content-Length : 표현 데이터의 길이
  - __표현 헤더는 전송, 응답 둘다 사용__

  > __Content-Type__
    - 미디어 타입, 문자 인코딩
    - ex. text/html; charset=utf8, application/json, image/png
  > __Content-Encoding__
    - 표현 데이터를 압축하기 위해 사용
    - 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가
    - 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제
