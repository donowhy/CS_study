# TCP/IP란

케이블 규격, IP 주소 지정 방법, 상대를 찾기 위한 방법 등을 표시하는 프로토콜을 모은 것을 `TCP/IP`라고 합니다.

TCP와 IP 프로토콜을 가리켜 `TCP/IP`라고 부르기도 하지만, IP 프로토콜을 사용한 통신에서 사용되고 있는 프로토콜을 총칭해서 `TCP/IP`라는 이름이 사용되고 있습니다.

## TCP/IP의 4계층

- 4계층 : 응용 계층(Application Layer)   
OSI 7계층의 세션 계층, 표현 계층, 응용 계층에 해당한다.   
TCP/UDP 기반의 응용 프로그램을 구현할 때 사용한다.   
프로토콜 – FTP, HTTP, SSH

- 3계층 : 전송 계층(Transport Layer)   
OSI 7계층의 전송 계층에 해당한다.   
장치 간에 **안정적**이고 **효율적**인 데이터 전달을 보장합니다.   
프로토콜 – TCP, UDP

- 2계층 : 인터넷 계층(Internet Layer)    
OSI 7계층의 네트워크 계층에 해당한다.    
통신 노드 간의 **데이터 패킷**을 전송하는 기능과 라우팅 기능을 담당한다.   
프로토콜 – IP, ARP, RARP

- 1계층 : 네트워크 액세스 계층(Network Access Layer or Network Interface Layer)   
OSI 7계층의 물리계층과 데이터 링크 계층에 해당한다.    
물리적인 주소로 MAC을 사용한다.   
프로토콜 - 이더넷, 와이파이, LAN, 패킷망