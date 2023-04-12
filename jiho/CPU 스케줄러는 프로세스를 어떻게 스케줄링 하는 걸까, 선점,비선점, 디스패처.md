cpu scheduler : cpu에서 실행될 프로세스를 선택하는 역활

nonpreemptive(비선점) scheduling

![img](.\img\선점비선점 .png)


신사적, 협력적, 느린 응답성

preemptive(비선점) scheduling

적극적, 강제적, 빠른 응답성, 데이터 일관성 문제

스케줄링 알고리즘

FCFS : 먼저 온것부터 서브

SJF : 프로세스의 다음 CPU burst가 가장 짧은 프로세스부터 실행

SRTF : 남은 CPU burst가 가장 짧은 프로세스부터 실행

priority : 우선순위가 높은 프로세스부터 실행

PR : time slice로 나눠진 CPU time을 번갈아가며 실행

multilevel queue : 프로세스들을 그룹화해서 그룹마다 큐를 두는 방식