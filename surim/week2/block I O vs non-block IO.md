# block I/O vs non-block I/O

Tags: 3주차

- I/O란
    
    데이터의 입출력 
    
- I/O의 종류
    - file
    - pipe
    - device
    - network(소켓):
        - 네트워크 통신을 위해 각 프로세스 안에 존재하며, 소켓을 통해 입출력을 할수 있
        - 백앤드 서버는 네트워크 상의 요청자들과 각 소켓을 열고 통신한다.
- block I/O: I/O작업을 요청한 프로세스/스레드는 요청이 완료될때까지 block됨 ex)팀장님이 검토 전까지 다른일할 수 없음
    
    ![Untitled](./%EC%9D%B4%EB%AF%B8%EC%A7%80/block.png)
    
    - 소켓에서 block I/O는? 소켓 A→소켓B를 보내려고 한다. 각 소켓에는 send buffer(보낼 데이터가 있는 메모리)와 recv_buffer(받는 데이터가 담긴 메모리)가 있음. 소켓A는 read할떄, recv버퍼가 비어있다면 block되고, 소켓s는 send버퍼에 자리가 생길 때까지 block됨
- non-block I/O : 프로세스/스레드를 block시키지 않고 요청에 대한 현재 상태를 즉시 리턴함 ex)팀장님 검토완료 전에 다른 일을 하고 있음
    
    ![Untitled](/surim/week2/%EC%9D%B4%EB%AF%B8%EC%A7%80/nonblock.png)
    
    - socket에서 non-block은? 소켓A의 recv버퍼에 데이터가 없는 상태에서 read를 하면 read시스템 콜은 바로 종료, 소켓 S도 send버퍼가 가득차도 write종료하고 다른 일을 함.
    - 타임갭이 발생: 커널이 작업을 완료했는데, 사용자가 그걸 가져가지 않아서, 다른 사용자가 커널을 쓸수 있는데 못쓰는 것
    - non-block I/O이슈: I/O작업 완료를 어떻게 확인할 것인지?
        1. 완료되었는지 계속 확인
            
            →완료된 시간과 완료를 확인한 시간 사이 갭으로 인해 처리속도가 느려질 수 있다. 
            
            → 계속 확인하는 것은 CPU낭비가 발생(여러개의 소켓을 가진 서버 입장에서는 굉장히 낭비)
            
        
        ⇒소켓이 만약 blocking모드일 경우, 한 소켓에 block이 되어 아무것도 처리하지 못하면 다른 클라이언트의 소켓에 데이터가 들어가도 처리하지 못한다
        
    1. I/O mutiplexing 다중입출력: 한번의 시스템콜로 관심있는 여러 I/O작업들을 동시에 모니터링하다가 그 중에 완료된 I/O작업들을 한번에 알려주는 방법
    - 종류: 1)epoll(리눅스) 2)kqueue(맥 os), IOCP(윈도우)
        
        ex) Linux epoll: epoll은 n개의 소켓에 데이터가 있다고 알려줌→스레드 풀의 여러개 스레드가 동시에 요청받아서 처리할 수 있음.
        
    - 네트워크 통신에 많이 사용
    1. callback/signal사용
        - POSIX AIO
        - LINUX AIO
        - 널리 사용되지는 않음
        - 데이터가 커널영역에서 유저영역으로 callback or signal됨
    2. io_uring 등.. 

⇒non-block I/O를 통해 I/O요청 완료전에도 다른 일을 할 수 있다.