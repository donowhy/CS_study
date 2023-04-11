- OS에서 프로세스 상태변화

![아무거나](./%EC%9D%B4%EB%AF%B8%EC%A7%80/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EC%83%81%ED%83%9C%EB%B3%80%ED%99%94.png)

출처:[https://devhan.tistory.com/m/103](https://devhan.tistory.com/m/103)

new→ ready→ running→ready→running…→I/O 혹은 critical section에 가기 위해 waiting→ready→running→terminated

*ready: cpu에서 실행되길 기다림

*os에서 스레드의 상태변화도 거의 동일

---

- JavaThread의 상태변화
    1. new: 아직 시작하지 않은 상태
    2. runnable: 실행중인 상태, 다른 리소스를 기다리는 상태도 포함(포괄적인 running상태)
    3. blocked: critical section에 들어가려고 모니터락을 얻기 위해 기다리는 상태
    4. waiting: 다른 스레드를 기다리는 상태 
        
        ex)Object클래스의 wait(모니터의 wait), thread클래스의 join메서드를 호출할 때
        
    5. timed_waiting: 제한시간을 두고 다른 스레드를 기다리는 상태
        
        ex)Object클래스의 wait with timeout(모니터의 wait), thread클래스의 join with timeout메서드를 호출할 때, thread의 sleep메소드 호출
        
    6. terminated: 종료된 상태
- Java thread dump: 실행중인 자바 프로세스의 현재 상태를 담은 스냅샷
    - 프로세스에 속한 여러스레드의 상태정보를 알 수 있다
    - 자바 API서버를 운영중인데, 자바 API의 스레드를 다 써버리고, 새 API요청에도 응답을 하지 못하면, 서버의 terminal에 접근해서 자바 instance의 thread dump를 확인해서 어디가 문제인지 분석할 수 있다.
