# 프로세스 동기화

---

## Race Condition(경쟁 조건)

여러 프로세스/스레드가 동시에 같은 데이터를 조작할 때 타이밍이나 접근 순서에 따라 결과가 달라질 수 있는 상황

## Synchronization(동기화)

여러 프로세스/스레드를 동시에 실행해도 공유 데이터의 일관성을 유지하는 것

## Critical Section(임계영역)

공유 데이터의 일관성을 보장하기 위해 하나의 프로세스/스레드만 진입해서 실행 가능한 영역

멀티 스레딩에 문제점에서 나오듯, 동일한 자원을 동시에 접근하는 작업(e.g. 공유하는 변수 사용, 동일 파일을 사용하는 등)을 실행하는 코드 영역을 Critical Section 이라 칭한다.

## Critical Section Problem(임계영역 문제)

프로세스들이 Critical Section 을 함께 사용할 수 있는 프로토콜을 설계하는 것이다.

### Requirements(해결을 위한 기본조건)

* Mutual Exclusion(상호 배제)  
  프로세스 P1 이 Critical Section 에서 실행중이라면, 다른 프로세스들은 그들이 가진 Critical Section 에서 실행될 수 없다.
* Progress(진행)  
  Critical Section 에서 실행중인 프로세스가 없고, 별도의 동작이 없는 프로세스들만 Critical Section 진입 후보로서 참여될 수 있다.
* Bounded Waiting(한정된 대기)  
  P1 가 Critical Section 에 진입 신청 후 부터 받아들여질 때가지, 다른 프로세스들이 Critical Section 에 진입하는 횟수는 제한이 있어야 한다. 제한이 없다면 독점 할 수 있다.

# 해결책

## Mutex Lock

* 동시에 공유 자원에 접근하는 것을 막기 위해 Critical Section 에 진입하는 프로세스는 Lock 을 획득하고 Critical Section 을 빠져나올 때, Lock 을 방출함으로써 동시에 접근이 되지 않도록 한다.

### 한계

* 다중처리기 환경에서는 시간적인 효율성 측면에서 적용할 수 없다.

## Semaphores(세마포)

* 소프트웨어상에서 Critical Section 문제를 해결하기 위한 동기화 도구

### 종류

OS 는 Counting/Binary 세마포를 구분한다

* 카운팅 세마포  
  **가용한 개수를 가진 자원** 에 대한 접근 제어용으로 사용되며, 세마포는 그 가용한 **자원의 개수** 로 초기화 된다.
  자원을 사용하면 세마포가 감소, 방출하면 세마포가 증가 한다.

* 이진 세마포  
  MUTEX 라고도 부르며, 상호배제의 (Mutual Exclusion)의 머릿글자를 따서 만들어졌다.
  이름 그대로 0 과 1 사이의 값만 가능하며, 다중 프로세스들 사이의 Critical Section 문제를 해결하기 위해 사용한다.

### 단점

* Busy Waiting(바쁜 대기)  
Spin lock이라고 불리는 Semaphore 초기 버전에서 Critical Section 에 진입해야하는 프로세스는 진입 코드를 계속 반복 실행해야 하며, CPU 시간을 낭비했었다. 이를 Busy Waiting이라고 부르며 특수한 상황이 아니면 비효율적이다.   
일반적으로는 Semaphore에서 Critical Section에 진입을 시도했지만 실패한 프로세스에 대해 Block시킨 뒤, Critical Section에 자리가 날 때 다시 깨우는 방식을 사용한다. 이 경우 Busy waiting으로 인한 시간낭비 문제가 해결된다.

### Deadlock(교착상태)

* 세마포가 Ready Queue 를 가지고 있고, 둘 이상의 프로세스가 Critical Section 진입을 무한정 기다리고 있고, Critical Section 에서 실행되는 프로세스는 진입 대기 중인 프로세스가 실행되야만 빠져나올 수 있는 상황을 지칭한다.

---