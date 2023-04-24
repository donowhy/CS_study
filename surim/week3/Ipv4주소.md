# Ipv4주소

- Ip:host에 대한 식별자, internet protocol
    - 버전: ipv4, ipv6
    - Network ID + host ID로 구성
    - 8bit 3자리씩 끊어 표기
    
    | Ipv4 | Ipv6 |
    | --- | --- |
    | 주소길이 32bit(=43억정도의 주소) | 128bit |
    | 현재 사용중 |  |
- net mask: network id 길이를 나타냄
    - 255.255.255.0처럼 넷마스크는 a,b,c클래스에 따라 달라지는데, 네트워크의 크기에 따라 다른 다른 클래스를 사용한다.
    - **넷마스크는 나라까지 식별할지, 시도까지 식별할지, 동까지 식별할지 등 어떤 주소를 참조할지를 식별하는 값**
    - Net id 네트워크 영역을 식별하기 위한 값
    - Host id 하나의 네트워크 영역에서 호스트를 식별하기 위한 값
    - ip와 서브넷 마스크의 bit의 and연산으로 네트워크 아이디의 길이를 알 수 있다.
    
    ![34E023A7-02C7-4C72-8512-4BB3D7D89497.png](/surim/week3/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/ipv4.png)
    
- CIDR표기법: xxxx.xxxx.xxxx.xxxx/net id길이