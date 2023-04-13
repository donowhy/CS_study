# CPU 스케줄러
CPU에서 실행될 프로세스를 선택하는 역할

### diapacher
선택된 프로세스에게 CPU를 할당하는 역할
1. Context switching
2. user mode 전환
3. 실행할 적절한 위치로 프로세스를 이동

### Nonpreemptive(비선점) scheduling VS Preemptive scheduling
| |Nonpreemptive|Preemptive|
|---|----|----|
| |프로세스가 자발적으로 running에서 나옴| 멱살잡고 끌어내릴수 있음 |
|특정|신사적, 협력적(cooperative)|적극적, 강제적, 빠른 응답성|
|단점|느린 응답성|데이터 일관성 문제|

### 스케줄링 알고리즘
>1. FCFS(first-come, first-served)   
       먼저 도착한 순서대로 처리
>2. SJF(shortest-job-first)   
    프로세스의 다음 CPU burst가 가장 짧은 프로세스부터 실행
>3. SRTF(shortest-remaining-time-first)   
    남은 CPU burst가 가장 짧은 프로세스부터 실행
>4. Priority   
우선순위가 높은 프로세스부터 실행
>5. RR(round-robin)   
time slice로 나눠진 CPU time을 번갈아가며 실행
>6. Multilevel queue   
프로세스들을 그룹화해서 그룹마다 큐를 두는 방식