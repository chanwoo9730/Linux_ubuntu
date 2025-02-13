# Linux top 명령어 (서버 상태 파악)

---

### TOP 명령어

---

top 명령어는 현재 OS의 상태를 나타내는 CLI 어플리케이션이다.

메모리 사용량, CPU 사용량 등을 나타내주며 top을 실행하는 동안에는 실시간에 근접한 내용을 보여준다.

![Untitled](https://user-images.githubusercontent.com/84123877/191898417-263b759f-24e4-4b86-8013-2652bed6303a.png)

### 요약 영역

---

![Untitled 1](https://user-images.githubusercontent.com/84123877/191898412-2380cc23-04b6-4f25-8d1b-8a7e94c31bd8.png)

> 각 영역에 대해 나타내는 값을 확인할 수 있다.
> 
- System time(시스템 현재 시간)
= GMT 기준 현재 시간을 나타낸다. (한국시간으로 +9)
- uptime(OS가 살아있는 시간)
= days와 시간으로 나타낸다.
- user sessions(유저 세션수)
= 접속중인 유저 세션 수이다. 좀 더 자세한 내용은 `who` 명령어를 통해 확인 가능하다
- Load Average
= CPU Load의 이동 평균을 표시한다. (100%를 넘긴다면, 처리못하고 대기중인 ps가 있다는것)
- Tasks
= 현재 프로세스들의 상태를 나태나는 영역이다.
- CPU 사용량
= Tasks 아래 %Cpu(s) 라는 영역이 있다. 각 요소는 다음과 같다. </br>

| us | 프로세스의 유저 영역에서의 CPU 사용률 |
| --- | --- |
| sy | 커널 영역에서의 CPU 사용률 |
| ni | 우선순위(priority) 설정에 사용하는 CPU 사용률 |
| id | 사용하고 있지 않는 비율 |
| wa | IO가 완료될때까지 기다리고 있는 CPU 비율 |
| hi | 하드웨어 *인터럽트에 사용되는 CPU 사용률 |
| si | 소프트웨어 인터럽트에 사용되는 CPU 사용률 |
| st | CPU를 VM에서 사용하여 대기하는 CPU 비울 |

* 인터럽트 : CPU가 특정 기능을 수행하는 도중에 급하게 다른 일을 처리하고자 할 때 사용할 수 있는 기능

- 메모리 사용량
= rem의 메모리 영역인 mem, 디스크를 메모리처럼 사용하는 Swap 영역이 존재한다.
(mem의 사용량이 가득 찼을때 swap 메모리 영역을 사용함, 디스크이기 때문에 rem보다 속도가 많이 느림)

### 디테일 영역

---

디테일 영역에는 각 프로세스에 대한 상세한 내용이 나온다.

- PID
= 프로세스 ID이며, 프로세스를 구분하기 위한 고유한 값이다.
- USER
= 해당 프로세스를 실행, 또는 효과를 받은 USER의 이름이다.
- PR & NI </br>
  - PR: 커널에 의해서 스케줄링디는 우선순위
  - NI: PR에 영향을 주는 nice라는 값
- VIRT, RES, SHR, %MEM </br>
  - 해당 필드는 프로세스의 메모리와 관련됨
  - VIRT: 프로세스가 소비하고 있는 총 메모리
  - RES: REM에서 사용중인 메모리 크기
  - SHR: 다른 프로세스와의 공유메모리(Shared Memory)
  - %MEM: RAM에서 RES가 차지하는 비율
- S
= 프로세스의 현재 상태를 나타낸다.
- TIME +
= 프로세스가 사용한 토탈 CPU 시간
- COMMAND
= 해당 프로세스를 실행한 커맨드를 나타낸다.

## Top 커맨드

---

### k - kill process

= top 화면을 보며 프로세스를 종료 가능하다.

### Sorting the process list

= 디테일 영역에 대해 원하는 값을 기준으로 정렬 방법을 제공한다.

- ‘M’ to sort by memory usage
- ‘P’ to sort by CPU usage
- ‘N’ to sort by process ID
- ‘T’ to sort by the running time
- ‘R’ to sort by 오름차순과 내림차순을 토글 변경한다.

### **Showing a list of threads instead of processes**

= ‘H’ 커맨드로 쓰레드(thread)를 기준으로 보여주는 방식이 변경된다.

### **Filtering through processes**

= ‘O’ or ‘o’ 커맨드로 필터링이 가능하다. 필터는 COMMAND, CPU 등 다양하게 가능하다.

![Untitled 2](https://user-images.githubusercontent.com/84123877/191898415-b7d26b0f-dde9-42f9-bf53-6e4aeb180248.png)

> MEM값이 2% 미만인 프로세스만 확인
> 

---
