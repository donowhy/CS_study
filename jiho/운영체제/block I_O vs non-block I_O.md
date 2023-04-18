# I/O : input/output

## network(socket)

    네트워크 통신은 socket을 통해 데이터 입출력

### backend server

    네트워크 상의 요청자들과 각각 소켓을 열고 통신

### block I/O

    I/O 작업을 요청한 프로세스/스레드는 요청이 완료될 때까지 블락됨
![img](.\img\block.png)


### non block I/O

    프로세스/스레드를 블락시키지 않고 요청에 대한 현재 상태를 즉시 리턴
![img](.\img\non-block.png)

#### non-block I/O 결과 처리 방식
    1. 완료됐는지 반복적으로 확인
        완료된 시간과 완료를 확인한 시간 사이의 갭으로 인해 처리 속도가 느려질수 있음
        완료됐는지 반복적 확인은 CPU낭비

    2.I/O multiplexing
        관심있는 I/O 작업들을 동시에 모니터링하고 그 중에 완료된 I/O작업들을 한번에 알려줌
            select - 잘 안쓰임
            poll - 잘 안쓰임
            epoll - 리눅스
            kqueue - 맥 OS
            IOCP(I/O completion port) - 윈도우/솔라리스

        네트워크 통신에 많이 쓰임
    
    3. Callback/signal 사용
        POSIX AIO
        LINUX AIO
        등등

        널리 사용되진 않음

    4. io_uring - 리눅스

    non-block I/O를 통해 I/O 요청 완료 전에도 다른 작업 가능
![img](.\img\2차원배열.png)<br><br>
    I/O를 요청한 쪽에서 챙기면 Synchronous<br>
    I/O를 요청한 쪽에서 챙기지 않으면 Asynchronous
    
