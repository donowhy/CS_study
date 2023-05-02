# Port 번호
- Process 식별자 ( 개발자 관점 )   

port번호 : socket 에 부여되는 정보
port번호는 16bit로 구성된다 (16bit = 0 ~ 65535)

TCP 에서 **Process**에 데이터를 넘겨줄 때
port번호를 통해 **Process**를 식별하여
**Process**의 `socket`에 데이터를 넘겨준다.

> ### 웹창을 여러개를 띄웠을 때의 port번호   
> 크롬이나 edge등 의 인터넷창은 탭마다 각각의 소켓을 가지고있고, 소켓마다 port번호가 다르다.

<hr>

## 일반적인 포트 번호
포트 번호는 크게 세 종류로 구분된다.

- 0번 ~ 1023번: 잘 알려진 포트 (well-known port)
- 1024번 ~ 49151번: 등록된 포트 (registered port)
- 49152번 ~ 65535번: 동적 포트 (dynamic port)

### well known port
20 : FTP(data)   
21 : FTP(제어)   
22 : SSH   
23 : 텔넷   
53 : DNS   
80 : 월드 와이드 웹 HTTP   
119 : NNTP   
443 : TLS/SSL 방식의 HTTP

> ### 웹에서의 표기   
>http://000.000.000.000   
>
>위와 같은 같은 월드 와이드 웹 URL은 기본적으로 80번 포트를 사용하므로 웹 브라우저는 자동적으로 이를 다음과 같은 의미로 처리한다.  
> 
>http://000.000.000.000:80