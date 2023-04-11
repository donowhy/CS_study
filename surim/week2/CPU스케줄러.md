- CPU 스케줄러: CPU가 놀지않고 일을 할 수 있도록 **cpu에서 실행될 프로세스 순서를 선택하는 역할**
    - 사용자가 프로그램 실행→프로세스 생성, READY상태(ready quque)
    - 스케줄러: 여기 READY 큐에서 어떤 프로세스가 cpu에 실행되어야할지 선택
- = dispatcher: ready→ running으로 상태가 바뀌면서 선택된 프로세스에게 **CPU를 할당하는 역할**
    
    ![구조2](./%EC%9D%B4%EB%AF%B8%EC%A7%80/%EA%B5%AC%EC%A1%B02.png)
    
    출처: [https://www.crocus.co.kr/1406](https://www.crocus.co.kr/1406) 출처
    
- 디스패처의 하는 일: context switching은 민감한 작업이라 커널모드에서 실행→ 새로운 선택된 프로세스가 실행될 수 있도록 user모드로 전환 → control을 새롭게 선택된 프로세스로 넘겨줌

? dispatcher와 scheduler의 차이는?

scheduler: 해야할 일을 정하는 것까지, dispatcher는 cpu를 프로세스에 할당하는 것이지만,

넓은 의미의 스케쥴링은 스케쥴러와 디스패처 기능을 동시에 말함

- 스케쥴링의 선점 방식
    
    
    |  | preemptive(선점)  | nonpreemptive(비선점) |
    | --- | --- | --- |
    |  정의 | 프로세스가 CPU에서 running 상태더라도 OS가 사용권을 강제 회수하고 선점할 수 있는 기능 | 프로세스 종료, I/O 등의 이벤트가 있을 때까지 실행을 보장(자발적으로 running상태에서 빠져나가는 경우**적극적, 강제적이지 않다 |
    | 경우 | 1) 멀티 태스킹 환경에서 프로세스가 time slice를 다 써서 다시 ready로 돌아와야한다면 다시 ready queue에 강제로 집어넣음 <br> 2) waiting에 있던 프로세스가 io작업이 끝나고 ready상태로 가게된 프로세스(A) 우선순위 >running하고 있는 프로세스(B) 우선순위 ⇒A를 cpu에서 실행시키고 B를 ready로 끌어내린다  <br><br> ex)Interrupt, I/O or Event Completion(이벤트가 끝나면 준비상태로 전환), I/O or Event Wait, Exit | 1) running상태의 프로세스가 종료 Exit <br> 2) 실행중인 프로세스가 I/O나 이벤트를 처리해야하는 경우, 이벤트가 모두 끝날때까지 대기상태를 만드는 것 I/O or Event Wait <br> 3) 자발적으로 다른 프로세스에게 양보할때 |
    | 장점 | 적극적, 강제적, 빠른 응답성(여러 프로세스가 cpu에서 자주 실행될 수 있도록 조정) | - 신사적 <br>- 협력적(cooperative_스스로 양보_프로그램의 협력의지가 필요) |
    | 단점 | 데이터 일관성 문제: cpu의 프로세스 상태를 강제로 바꾸기 때문에 데이터 일관성 문제→ 임계영역, 뮤텍스 등을 만들어야 함 | 느린응답성: 프로세스가 cpu를 다 쓸때까지 기다려주기 때문에, 다른 프로세스는 계속 ready queue에서 기다리고 있음=사용자입장에서는 응답이 느림 |

스케줄링 알고리즘: ready queue에서 기다리고 있는 프로세스를 어떤 기준으로 선택할건지

1. FCFS(first come first start) 먼저온것부터 먼저 처리 like queue
2. SJF(shortest job first): 프로세스의 다음 cpu burst가 가장 짧은 프로세스부터 가장 먼저 실행
3. SRTF(shortest remaining time first): 남은 cpu burst가 가장 짧은 프로세스부터 실행: SJF+preemptive(선점)방식 결합
    
    ex)프로세스가 실행되던 중 선점이 되어서 남아있을 때, 남아있는 cpu burst가 짧은 것부터 실행
    
4. priority: 우선순위가 높은 프로세스부터 실행
    
    *선점, 비선점 방식에 따라 처리하는 순서가 달라지기도 한다. ex)새로운 프로세스가 기존 프로세스보다 우선순위가 높을 경우
    
5. RR(round-robin): time slice로 나눠진 CPU burst time을 번갈아가며 실행 (like 멀티태스킹)
6. mutilevel queue(다단계 큐): 프로세스들을 그룹화해서 그룹마다 큐를 두는 방식
    - 우선순위가 높은 큐는 작은 time quantum을 할당하고, 우선순위가 낮은 큐는 큰 time quantum을 할당해서 우선순위가 낮은 큐들이 실행 못하는 걸 방지함
