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

프로세스 제어 블록:

- 프로세스 젱 블록은 프로그램이 프로세스로 전환 될 때 운영체제가 만드는 작업 지시서
- 어떤 프로그램이 프로세스가 되었다는 것은 운영체제로부터 프로세스 제어 블록을 받았다는 의미
- 프로세스 제어 블록에 있는는 대표적인 세 가지
  - 1
  - 2
  - 3

프로세스의 네 가지 상태

- 생성 상태
- 준비 상태
- 실행 상태
- 완료 상태

휴식 상태와 보류 상태

- 휴식 상태: 프로세스가 작업을 일시적으로 쉬고 있는 상태
- 보류 상태: 프로세스가 메모리에서 잠시 쫓겨난 상태로 '일시 정지 상태'라고도 불림
