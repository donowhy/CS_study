# 모니터
mutual exclusion을 보장
조건에 따라 스레드가 대기 상태로 전환 가능

## 언제
- 한번에 하나의 스레드만 실행돼야 할 대
- 여러 스레드와 협업이 필요할 때

## 구성 요소
- mutex
>critical section에서 mutual exclusion을 보장하는 장치   
>mutex lock을 취득하지 못한 스레드는 큐에 들어간 후 대기 상태로 전환   
>mutex lock을 쥔 스레드가 lock을 반환하면 락을 기다리며 큐에 대기상태로 있던 스레드중 하나가 실행

- condition variable
>waition queue를 가짐
조건이 충족대길 기다리는 스레드들이 대기 상태로 머무는 곳

### condition variable 주요 동작

- waite   
thread가 자기 자신을 condition variable의 waiting queue에 넣고 대기상태로 전환

- signal   
waiting queue에서 대기중인 스레드 하나를 깨움

- broad   
waiting queue에서 대기중인 스레드 전부를 깨움

<hr>

## 컨슈머 프로듀서 문제

Consumer-Producer 문제는 생산자(Producer) 스레드와 소비자(Consumer) 스레드 간의 데이터 공유 문제입니다. 생산자 스레드는 데이터를 생성하고, 소비자 스레드는 데이터를 소비합니다. 이때, 생산자 스레드와 소비자 스레드가 동시에 데이터에 접근할 수 있으므로 데이터의 일관성을 보장하기 위해서는 동기화가 필요합니다.


### 해결 방법

1. 생산자 스레드는 Monitor의 데이터를 설정하는 메서드를 호출하여 데이터를 생성합니다.

2. 소비자 스레드는 Monitor의 데이터를 반환하는 메서드를 호출하여 데이터를 소비합니다.

3. Monitor는 데이터를 저장하고 있는 변수와 조건 변수를 갖고 있습니다. 생산자 스레드는 데이터를 생성한 후, 조건 변수를 통해 소비자 스레드가 데이터를 소비할 때까지 기다리도록 합니다. 소비자 스레드는 데이터를 소비한 후, 조건 변수를 통해 생산자 스레드가 데이터를 생성할 때까지 기다리도록 합니다.
