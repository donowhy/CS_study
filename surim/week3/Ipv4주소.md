# Ipv4주소

- Ip:host에 대한 식별자, internet protocol
    - 버전: ipv4, ipv6
    - Network ID + host ID로 구성
    - 8bit 3자리씩 끊어 표기
    
    | Ipv4 | Ipv6 |
    | --- | --- |
    | 주소길이 32bit(=43억정도의 주소) | 128bit |
    | 현재 사용중 |  |
- Subnet mask(=net mask): network id 길이를 나타냄
    - Net id 네트워크 영역을 식별하기 위한 값
    - Host id 하나의 네트워크 영역에서 호스트를 식별하기 위한 값
    - ip와 서브넷 마스크의 bit의 and연산으로 네트워크 아이디의 길이를 알 수 있다.
    
    ![34E023A7-02C7-4C72-8512-4BB3D7D89497.png](Ipv4%E1%84%8C%E1%85%AE%E1%84%89%E1%85%A9%20faaa650b3b6e4dd2a84dfe3591cf601a/34E023A7-02C7-4C72-8512-4BB3D7D89497.png)
    
- CIDR표기법: xxxx.xxxx.xxxx.xxxx/net id길이