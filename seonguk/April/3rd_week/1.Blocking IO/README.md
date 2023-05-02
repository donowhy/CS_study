# Blocking I/O
I/O 작업을 요청한 프로세스/스레드는
요청이 완료될 때까지 블락됨

파일에 데이터 요청
OS가 데이터를 읽고 돌려 보낼 때 까지
Process가 작동을 안함(Block)

# NonBlocking I/O
프로세스/스레드를 블락시키지 않고
요청에 대한 현재 상태를 즉시 리턴

## 완료됬는지 확인 어떻게?
### 1. 반복적으로 확인
- time gap 이 생겨서 딜레이됨
- 반복적으로 확인해서 CPU낭비가 발생

### 2. I/O multiplexing
관심있는 I/O 작업들을 동시에 모니터링 하고
그 중에 완료된 I/O 작업들을 한번에 알려줌

#### 종류
1. select (안씀)
2. poll (안씀)
3. epoll (리눅스)
4. kqueue (맥)
5. IOCP(I/O completion port) (윈도우)

### 3. callback 혹은 signal사용
#### 종류
1. POSIX AIO
2. LINUX AIO






소켓
네트워크통신용 입출력

User ------------------- User socket

Kernel ----------------- Server socket

H/W -------------------- Server database