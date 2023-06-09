## 용어
- 운영체제: 컴퓨터 시스템, HW관리, 응용프로그램과 HW 간 인터페이스 역할 등하며 컴퓨터가 운영을 어떻게 하는지에 대한 체제
    =사용자가 컴퓨터를 편리하고 효과적으로 사용할 수 있도록 환경을 제공하는 시스템 SW
    
    - 종류: 윈도우, 리눅스, UNIX 등

- CPU: 명령어를 실행하는 연산장치(=프로세서)
- 메인메모리: 프로세스가 CPU에서 실행되기 위해 대기하는 곳
- I/O : 파일을 읽고 쓰거나 I/O장치와 데이터를 주고받는것, 네트워크와 데이터를 주고받는것
- 캐시 적중률: 요청 수(cpu가 주기억장치에 접근해야하는 전체 횟수)와 비교해 (메모리 접근없이) 캐시장치 접근으로 충족될 수 있는 횟수의 비율 
- 어플리케이션: 특정 업무를 수행하기 위해 만든 프로그램

## 프로그램과 프로세스
- 프로그램: 컴퓨터가 실행할 수 있는 명령어의 집합 (like 피자의 레시피)
- 프로세스: 컴퓨터에서 실행중인 프로그램, 각각 프로세스는 독립된 메모리 공간을 할당받음(like 피자)
    - 프로세스의 메모리 내 4가지 영역
        - code: 실행명령
        - data: static, global 변수를 담음
        - heap: 동적 메모리 영역
        - stack: 지역변수, 매개변수, 반환 값 등 일시적인 데이터
    - PCB블럭: 프로세스에 대한 정보를 담고 있음. 프로세스가 만들어질 때 생성
        - 포인터(대기상태 큐를 구현하기 위해 필요한 포인터), process state(현재 상태), PID(고유번호), Program Counter(다음 명령어)

## 프로세스 시스템 종류
- 단일 프로세스 시스템: CPU는 한번에 하나의 처리만 가능→ 단일 프로세스 시스템은 한번에 하나의 프로그램만 실행되서 CPU사용률이 좋지 않음
- 멀티프로그래밍: 여러프로그램이 동시에 실행된다→but cpu사용시간이 길어지면 다른 프로세스는 계속 대기함
- **멀티태스킹**→ cpu의 시간을 아주 작게 쪼개서 여러개의 프로세스를 실행시키자→ 프로세스의 응답시간을 최소화함=동시에 실행되는 것처럼 보임
- 동시성: 한개의 CPU가 짧은 순간에 프로세스 or 스레드가 번갈아가면서 진행(context switching)해서 동시에 하는 것처럼 보이게 함
    - **멀티프로세스**: 여러개의 프로세스를 활용하는 시스템(like 여러 사용자가 하나의 사이트에 로그인하려고할때, 여러개 프로세스가 처리)
        
        ***멀티프로세싱**: 여러개의 프로세서나 코어를 활용
        
    - **멀티스레딩**: 여러개 스레드가 동시에 여러 작업을 실행. 스레드에 문제가 생기면 전체 프로세스에 영향이 감(like explorer의 작동이 중지되었습니다..)
    
    | 멀티스레드 | 멀티프로세스 |
    | --- | --- |
    |  | ipc를 사용한 통신 |
    | 공유된 자원으로 메모리 효율적, 통신 비용 절감 | 자원소모적, 개별 메모리 차지 |
    | 컨텍스트 스위칭 비용이 적음 | context switching 비용이 큼 |
    | 공유 자원 관리를 해야함(동기화 문제) | 동기화 작업이 필요하지 않음 |
    | 오류로 인해 하나의 스레드가 종료되면 전체 스레드가 종료될 수 있다  | 하나의 프로세스가 죽어도 다른 프로세스에는 영향x |
- **멀티코어**:병렬처리- 2개 이상의 코어에서 동시에 1개 이상의 프로세스(스레드)가 한꺼번에 진행되는 것
- 쓰레드: 경량화된 프로세스. 1개 프로세스 내 하나이상의 cpu에서 실행되는 실행단위
    - 하나의 프로세스 안 여러개 쓰레드가 있으면, 각 쓰레드는 스택부분만 따로 가지고 있고, 나머지를 공통된 자원으로 사용함
    
    =컨텍스트 스위칭이 있을 때,  캐시적중률이 올라간다 = 컨텍스트 스위칭이 가볍다
    
    (like 하나의 회의실에 모니터, 본체를 나두고 마우스, 키보드만 연결하면 그 자리를 사용할 수 있음) 
    
