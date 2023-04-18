# Synchronous(동기)
    여러 작업들을 순차적으로 실행하도록 개발
![img](.\img\synchronous.png)

# Asynchronous(비동기)
    여러 작업들을 독립적으로 실행하도록 개발
![img](.\img\asynchronous-1.png)
![img](.\img\asynchronous-2.png)
![img](.\img\asynchronous-3.png)
![img](.\img\asynchronous-4.png)

    Asynchronous != multithreding

    Asynchronous
     여러 작업을 동시에 실행하는 프로그래밍 방법론

    multithreding
     Asynchronous 의 한 종류
    
    이를 가능하게 하는건 multi-threads, non-block I/O

<br>

## 백엔드 프로그래밍의 추세는 스레드를 적게 쓰면서도 non-block I/O를 통해 전체 처리량을 늘리는 방향으로 발전 중
<br>
<br>

# OS 관점
## 1. synchronous I/O = block I/O, asynchronous I/O = non-block I/O
## 2. Synchronous I/O : 요청자가 I/O 완료까지 챙겨야 할 때, Synchronous I/O : 완료를 noti 주거나 callback으로 처리
## 3. asynchronous I/O : block I/O 를 다른 thread 에서 실행
<br>
<br>

# 백엔드 관점
## 하나의 서비스는 기능과 역활에 따라 여러 개의 마이크로 서비스로 구성되고 이들 사이에는 빈번하게 커뮤니케이션이 발생
