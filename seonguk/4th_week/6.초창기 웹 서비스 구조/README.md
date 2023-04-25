# Web서비스
HTML(문서구조) + HTTP(통신 프로토콜)

만든 이 : [팀 버너스리](https://ko.wikipedia.org/wiki/%ED%8C%80_%EB%B2%84%EB%84%88%EC%8A%A4%EB%A6%AC)

## (문서를 다루는) 프로그램의 구성요소
- 자료구조
- UI
- 제어

### why
> `유지보수`의 편의성을 위해서

<hr>

## HTTP 전송 방식
웹 클라이언트 - 인터넷 - 웹 서버

TCP/IP `연결`(+상태) -> HTTP 통신 (***Stateless***)

### 통신 순서
1. 클라이언트가 Application 에 URL입력
2. DNS 가 URL을 Server IP 로 해석
3. IP가 가리키는 Server에 GET형태로 요청
4. Server가 HTML문서를 클라이언트에게 전송
5. 클라이언트가 HTML문서를 해석
6. 구문분석 -> 자료구조 (비선형) DOM
7. Application에 렌더링

일련의 과정이 HTML문서 뷰어와 동일하게 작동

>### 차이점   
>서버와의 통신을 통해 원격 뷰어의 기능