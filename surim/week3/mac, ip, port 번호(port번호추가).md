# mac, ip, port 번호(port번호추가)

Tags: 3주차, 4주차

## HW관점

### Mac: 하드웨어의 주소→NIC(네트워크 인터페이스 카드=LAN카드)에 대한 식별자

*호스트는 LAN카드를 여러개 가질 수 있는데, 이 mac주소를 자주 바꾸지 않은다, 그리고 하드웨어의 맥주소도 바꿀 수 있다

---

## SW관점

### IP:네트워크계층의 주소→ **호스트에 대한 식별자**

*호스트: 인터넷에 연결된 컴퓨터

****ip주소는 n개가 있을 수 있다,**

 NIC 1개에 ip주소를 여러개 바인딩해서 쓸 수 있다(=컴퓨터 하나에 여러개의 ip주소가 있을 수 있다)

### Port: 전송계충의 주소 → 프로세스에 대한 식별자

여러가지 형태로 식별의 대상이 달라진다(sw개발자:process식별자?, 네트워크 관리자: 서비스?(특정 프로토콜(서비스)를 요청하는 서비스):, 하드웨어: 인터페이스 번호?

- TCP 소켓에 들어있으면서(attach) 통신하는 프로세스를 식별한다
- **소켓:** 컴퓨터 네트워크에서 **프로세스 간 통신의 종착점**(end point)을 의미. 그 단말은 데이터전송을 위한 인터페이스 역할을 함
    - 양방향통신을 위해 **IP주소와 포트번호의 조합**으로 식별됨.
    - 클라이언트는 **서버의 IP주소와 포트번호를 사용해서 서버 소켓에 연결 요청** → 서버 소켓은 **클라이언트 요청 수신**하고, 이를 처리하기 위한 **새로운 소켓을 생성**
        - 소켓에 부여할 포트번호는 서버는 개발자가 지정해서 부여하고, 클라이언트는 os가 포트번호를 정해준다
    - 대표적인 소켓 프로토콜: TCP, UDP
    1. ? 소켓은 파일일까 인터페이스일까? 소켓은 파일과 유사하게 ‘읽기’와 ‘쓰기’ 동작하며 입출력을 수행할 수 있지만, 
        
        네트워크에서 데이터를 전송하기 위해 특정한 규약(프로토콜)을 사용하고, 이를 위한 여러가지 기능들을 제공한다는 점에서 파일은 아니고, 네트워크 통신을 위한 별도의 인터페이스이다.
        
    2. ? 소켓과 패킷의 다른점은?
    - 소켓: 네트워크 통신할 수 있는 인터페이스, 소켓을 이용해 데이터 전송/수신 가능
    - 패킷: 소켓을 통해 전송되는 데이터를 전송하는 단위
    1. ? 모든 프로세스가 http통신을 하면 같은 포트번호를 쓰는 것 아닌가?
        
        만약 모든 프로세스들이 http 통신을 한다면, 기본적으로 모두 80번 포트라는 서비스 포트를 지정받을 수 있습니다. 그리고 이후에는 서로를 식별하기 위해 프로세스 식별자 포트를 이용합니다. 예를 들어, 엣지 프로세스는 80번 포트(서비스 포트)와 30000번 포트(프로세스 식별자 포트)를 이용하고, 크롬 프로세스는 80번 포트(서비스 포트)와 30001번 포트(프로세스 식별자 포트)를 이용할 수 있습니다.
        
        포트 번호는 한 Host 내에서 같은 번호를 여러 프로세스가 사용하지 못하는 것이 이슈인데 만일 같은 번호를 쓰더라도 IP주소가 다른 호스트라면 문제가 되지 않습니다.
        
    2. ? PID와 포트의 차이점은?
        
        PID는 운영 체제 내부에서만 사용하는 프로세스 식별자이고, 포트는 네트워크 통신에서 사용됩니다. 
        
- port번호는 16bit로 표현되며, 2^16 - 2 개 번호를 사용한다
![Untitled](/surim/week3/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/mac_ip_port.png)