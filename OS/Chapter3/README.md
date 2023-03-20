# 프로세스와 스레드

<br/>
<hr/>
<br/>

## 프로세스의 개요

<br/>

프로그램:

- 저장장치에 저장되어 있는 정적인 상태

프로세스:

- 실행을 위해 메모리에 올라온 동적인 상태

## 요리사 모형의 비유

<br/>

주문서의 역할:

일괄 작업 방식의 요리:

시분할 방식의 요리:

- 요리사 1명이 시간을 적당히 배분하여 여러 가지 요리를 동시에 하는 방식

- 요리사는 주문 목록에 있는 주문서 중 하나를 가져다가 요리함

- 모든 요리가 제공되면 주문 목록에서 삭제

<br/>

Thread:

- 운영체제로부터 시스템 자원을 할당받는 작업의 단위
  <br/>
  |Process|
  |------|
  ||
  |Code|
  |Data|
  |Stack|
  |Heap|

- 한 프로세스 내에서 동작되는 여러 실행의 흐름으로 프로세스 하나에 자원을 공유하면서 일련의 과정을 여러 개를 동시에 실행시킬 수 있는 것

Process
<br/>
Code Data Heap
<br/>
|Thread1|
|---|
|Process|
<br/>
<br/>
|Thread2|
||
|Process|
<br/>

<img src="https://cdn1.byjus.com/wp-content/uploads/2022/08/word-image-15.png">

PCB(Process Control Block)

## 프로그램에서 프로세스로의 전환

<br/>

fork() 시스템 호출의 개념:

- 1
- 2

fork() 시스템 호출을 하면 프로세스 제어 블록을 포함한 부모 프로세스 영역의 대부분이 자식 프로세스에 복사되어 똑같은 프로셋가 만들어짐
<br/>
단, 프로세스 제어
<br/>

fork()시스템 호출의 장점

- 프로세스의 생성 속도가 빠름
- 추가 작업 없이 자원을 상속할 수 있음
- 시스템 관리를 효율적으로 할 수 있음

```C
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(){

    printf("L0\n");
    fork();
    printf("L1\n");
    fork();
    printf("Bye\n");
}
```

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdwju7Q%2Fbtrw44J1wRu%2FKx8UYtXkGsbq7VmUfMCf1k%2Fimg.png">

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(){

    pid_t pid;
    int x = 1;

    pid = fork();
    if(pid == 0){ /*Child*/
        printf("child: x=%d\n", ++x);
        exit(0);
    }

    /*Parent*/
    printf("parent: x=%d\n", --x);
    exit(0);
}
```

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAfbru%2FbtrwWf6SJKr%2FFd7MzD5Nt2Qk2agQG1nWQ0%2Fimg.png">

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fphv8y%2FbtrgoYslu0C%2F4Cw3FKqGK5o8OrGVEKjef0%2Fimg.png">

<br/>

```c
#include <stdio.h>
#include <sys/types.h>
int main(){
    fork();
    fork();
    fork();
    printf("안녕");
    return 0;
}
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(){

    printf("L0\n");
    if(fork() == 0){
        printf("L1\n");
        if(fork() == 0){
            printf("L2\n");
        }
    }
    printf("Bye\n");
}
```

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcsZmtP%2FbtrwVsMabsC%2FLvgKoaOMfAEKB8OWlZMxtk%2Fimg.png">
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcmjtyF%2FbtrgkTr2Bkt%2F6RWVoJ1Q8dm4rmOCDOqWBK%2Fimg.png">
<br/>

exec() 시스템 호출의 개념:

- 기존의 프로세스를 새로운 프로세스로 전환(재사용)하는 함수
  - fork(): 새로운 프로세스를 복사하는 시스템을 호출
  - exec(): 프로세스는 그대로 둔 채 내용만 바꾸는 시스템 호출

exec() 세스템 호출의 동작 과정

- exec() 시스템 호출을 하면 코드 영역에 있는 기존의 내용을 지우고 새로운 코드로 바꿔버림
- 데이터 영역이 새로운 변수로 채워지고 스택 영역이 리셋
- null

  <br/>

프로세스 제어 블록:

- 프로세스를 실행하는 데 필요한 정보를 보관하는 자료 구조
- 프로세스는 고유의 프로세스 제어 블록을 가짐
- 프로세스 생성 시 만들어져서 프로세스가 실행을 완료하면 폐기

- 프로세스 제어 블록은 프로그램이 프로세스로 전환 될 때 운영체제가 만드는 작업 지시서
- 어떤 프로그램이 프로세스가 되었다는 것은 운영체제로부터 프로세스 제어 블록을 받았다는 의미
- 프로세스 제어 블록에 있는는 대표적인 세 가지

프로세스 제어 블록의 구성:

- 메모리 관리 정보
- 할당된 자원 정보

- 계정 정보
- 부모 프로세스 구분자와 자식 프로세스 구분자

프로세스의 네 가지 상태

- 생성 상태
- 준비 상태
- 실행 상태
- 완료 상태

휴식 상태와 보류 상태

- 휴식 상태: 프로세스가 작업을 일시적으로 쉬고 있는 상태
- 보류 상태: 프로세스가 메모리에서 잠시 쫓겨난 상태로 '일시 정지 상태'라고도 불림

<img src="https://blog.kakaocdn.net/dn/bPZKGg/btqEInKEMAp/LMmm4H2rp8HOEtgy5WKeg1/img.png">

프로세스를 바꿔주는 일을 하는것이 스케줄러이고,<br/>
스케줄러가 프로세스를 바꿔주는 것을 문맥교환이라한다.

## 프로세스의 구조

- 코드 영역
  - 프로그램의 본문이 기술된 곳
  - 프로그래머가 작성한 코드가 탑재되며 탑재된 코드는 읽기 전용으로 처리됨
- 데이터 영역
- 스택 영역

프로세스의 계층 구조의 장점

- 프로세스의 재사용이 용이함
- 자원 회수가 쉬움
  - 프로세스를 계층 구조로 만들면 프로세스 간의 책임 관계가 분명해져서...

고아 프로세스와 좀비 프로세스

- 고아 프로세스: 부모 프로세스가 먼저 종료되어 돌아갈 곳이 없는 프로세스
- 좀비 프로세스: 자식 프로세스가 종료되었는데도 부모 프로세스가 뒤처리를 하지 않아 발생하는 프로세스
- c언어에서는 exit() 또는 return()문을 사용해 자식 프로세스의 작업이 끝났음을 부모 프로세스에 알림

스레드의 정의:

- CPU 스케줄러가 CPU에 전달하는 일 하나

- CPU가 처리하는 작업의 단위는 프로세스로부터 전달받은 스레드
  - 운영체제 입장에서의 작업 단위는 프로세스
  - CPU 입장에서의 작업 단위는 스레드

프로세스의 스레드의 차이

- 프로세스끼리는 약하게 연결되어 있는 반면 스레드끼리는 강하게 연결

스레드 관련 용어

- 멀티스레드
- 멀티태스킹: 운영체제가 CPU에 작업을 줄 때 시간을 잘게 나누어 배분하는 기법
- 멀티 프로세싱:
- CPU 멀티스레드

멀티스레드의 장점

- 응답성 향상
- 자원 공유
- 효율성 향상

멀티 스레드의 단점

- 모든 스레드가 자원을 공유하기 때문에 한 스레드에 문제가 생기면 전체 프로세스에 영향을 미침

- 인터넷 익스플로러에서 여러 개의 화면을 동시에 띄었는데 그중 하나에 문제가 생기면 인터넷 익스플로러 전체가 종료
