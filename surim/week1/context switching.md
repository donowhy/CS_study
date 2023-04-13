## context switching
- 컨텍스트 스위칭: CPU/코어에서 실행중이던 프로세스/스레드가 다른 프로세스/스레드로 교체해서 여러 프로세스/스레드를 동시에 실행시키기 위함
- 컨텍스트: 프로세스/ 스레드의 CPU, 메모리에서 상태

- 컨텍스트 스위칭은 언제 발생?
    주어진 time slice를 다 사용했거나 I/O작업을 하거나 다른 리소스를 기다려야할 때 발생
- 컨텍스트 스위칭을 누구에 의해 실행?
    OS의 커널(각종 리소스를 관리 감독하는 역할)
- 실행과정에 따라 분류: 1. 프로세스 컨텍스트 스위칭, 2. 스레드 컨텍스트 스위칭
    - 공통점:
        - 커널모드에서 실행(context switching이 일어나면서 프로세스가 컴퓨터의 리소스가 필요하면 커널에 통제권을 넘겨줘서 커널에서 실행)
        - 프로세스 별로 cpu의 레지스터 상태를 교체(프로세스 실행에 필요한 데이터를 따로 저장해놓고 교체한다)

|  | 프로세스 컨텍스트 스위칭 | 스레드 컨텍스트 스위칭 |
| --- | --- | --- |
| 차이점 | 가상메모리 주소 관련 처리를 추가로 수행 | 메모리 주소 관련 처리를 하지 않아 프로세스 컨텍스트 스위칭보다 더 빠르다 |
|  | *프로세스는 각각의 메모리를 가지고 있기 때문에 MMU가 P2의 메모리를 바라보도록 하고, TLB를 비움
→그렇게 해야 P1이 끝나고 P2가 진행될때 자신의 메모리 영역에 접근할 수 있음 |  |

- 컨텍스트 스위칭이 미치는 간접적인 영향: 캐시 오염(서로 다른 데이터들이 교체되면서 캐시가 오염됨 → 자주일어나면 좋지 않다.
    
    *캐시: 자주쓸것같은건 CPU의 캐시에 저장해놓기 때문에 메모리에 접근하지 않아도 데이터를 불러올 수 있음
    
- 유저관점에서 컨텍스트 스위칭은 단지 순수한 오버헤드 처럼 보이기 때문에 자주 수행하면 좋지 않다(수행하는 동작과 상관없이 CPU만 잡아먹는다)