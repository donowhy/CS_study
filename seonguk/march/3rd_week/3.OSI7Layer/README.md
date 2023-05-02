# 네트워크
공부하지마라

| 개념 | 사실 |
| --- | --- |
| 사람 | 최호성 |
|OSI 7 Layer | TCP/IP + HTTP|

## 소켓
TCP/IP를 유저모드 application process가 접근할 수 있도록 파일형태로 추상화한 것

![model image](images/graph.png)
## OSI 7 Layer
|  | OSI 7 Layer |
| --- | --- |
| User | L7 <br> L6 <br> L5 |
| --- | --- |
| Kernel | L4 ( Transport ) <br> L3 ( Network ) |
| --- | --- |
| H/W | L2 <br> L1 |

## DOD

|  | DOD |
| --- | --- |
| User | Application |
| --- | --- |
| Kernel | Transport <br> Network |
| --- | --- |
| H/W | Access |

## 구현

|  | 구현 |
| --- | --- |
| User | Process <br> File(Socket) |
| --- | --- |
| Kernel | TCP/IP <br> Driver |
| --- | --- |
| H/W | NIC |