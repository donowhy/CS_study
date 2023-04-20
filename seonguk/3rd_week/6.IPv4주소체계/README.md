# IP주소
Host에 대한 식별자
(Internet Protocol)

- IPv4
주소길이 : 32bit

표기법 : 8bit 씩 끊어서 표시
192.168.0.1
<-net ID(24bit)->|<-Host ID(8bit)->

Net Mask = net ID의 길이 
255.255.255.0

Net ID와 Net Mask를 AND연산하여
네트워크 주소를 얻을수 있다.
==
192.168.0.1 / 24
이렇게 표기하기도 함

- IPv6
주소길이 : 128bit
