# 오픈소스SW 과제 3 리눅스 명령어 조사

## 1. top 

리눅스에서 top 명령어는 OS의 상태를 확인하는 명령어 입니다.
실제 linux 환경에서 top 명령어를 실행해보면,
<img width="862" alt="top" src="https://github.com/user-attachments/assets/f05891e4-2b86-439b-bf38-72c198b023d5" />
위 이미지와 같이 OS 상태창이 나오게 됩니다.
다른 특정 옵션 없이 사용한 결과로, 이는 3초의 인터벌을 가지며 업데이트가 지속적으로 됩니다.
이러한 지속적인 업데이트를 사전에 옵션을 통해 바꿀 수 도 있습니다.
top에는 사전 명령어인 -b, -n이 있습니다.
-b는 batch 모드, -n은 뒤에 숫자를 붙여서 몇 번 반복을 할지를 정하는 옵션입니다.
top을 실행한 상태에서도 명령어를 입력할 수 있습니다.

|    명령어    |        설명            |
|-------------|-----------------------|
|  shift+p  |  CPU 사용률 내림차순  |
|  shift+m  |  메모리 사용률 내림차순  |
|  shift+t  |  프로세스가 돌아가고 있는 시간순  |
|  k  |  입력 후 PID 숫자 입력 하면 프로세스 종료  |
|  a  |  메모리 사용량에 따른 정렬  |
|  b  |  batch 모드로 전환  -b와 동일 |
|  1  |  CPU Core 별로 사용량 확인  |

위 표와 같은 명령어를 이용해서 top 사용중에도 나오는 정보를 바꿀 수 있게 됩니다.

top 과 같은 기능은 window에서도 쉽게 찾아볼 수 있는데, 
흔히들 프로그램이 먹통이거나 할 때 누구나 클릭해본 작업관리자가 이와 같은 역할을 하고 있다고 볼 수 있습니다.

## 2. ps

process status의 약자로 현재 사용중인 프로세스 정보를 확인할 수 있습니다.
이는 top과도 비슷하다고 볼 수 있습니다만, 실제로 ps를 다른 옵션 없이 사용을 해보자면

<img width="254" alt="ps" src="https://github.com/user-attachments/assets/7119c439-c56d-480b-a2b5-3252652b1f5b" />

이와 같이 정말 짧은 줄만 나오게 됩니다. 
위에 나온 정보는 지금 캡처된 shell에서 실행한 것에 대한 정보만을 보여주는 것이며, 
ps의 풀네임과 같이 status를 그 순간에 실행된 것만 캡처해서 보여주는 형태로 나오게 됩니다.

ps에도 3가지 명령어가 있습니다. 
|  명령어  |  설명  |
|---|---|
|  -e  |  현재 shell 뿐만 아닌 전체의 프로세스 정보 출력  |
|  -f  |  보다 상세한 정보 출력  |
|  -l  |  -f보다 상세한 정보 출력  |

이렇게 3가지 명령어가 있으며, 이는 ps -e -f -l 과 같은 형태가 아닌, ps -efl 과 같은 형태로도 바로 실행이 가능합니다.
<img width="854" alt="ps efl" src="https://github.com/user-attachments/assets/1de27e48-e2c0-48a5-b78e-99803c1e546e" />

## 3. jobs

이는 백그라운드 작업의 상태를 표시하는 명령어입니다.
linux shell을 실행한 직후 바로 jobs 명령어를 써보면

<img width="565" alt="jobs" src="https://github.com/user-attachments/assets/a38b32c3-9304-4c64-af7d-aa139e2b3140" />

이처럼 아무것도 안 나옵니다.
현재 백그라운드에 실행된 것이 없다는 걸 의미합니다. 
그럼, 백그라운드에 ping 8.8.8.8 & 를 이용해서 구글에 ping을 날리면서 jobs 명령어를 실행해보면

<img width="440" alt="jobs2" src="https://github.com/user-attachments/assets/ac92eea1-ad36-4172-8690-07c3f41af9fe" />

이와 같이 Running ping 8.8.8.8 & 라고 뜨는 걸 확인할 수 있습니다.

jobs의 명령어를 보자면
|  명령어  |  설명  |
|---|---|
|  -l  |  PID와 JOB 목록 출력  |
|  -n  |  프로세스 그룹 중 대표 PID 출력  |
|  -p  |  JOB의 PID만 출력  |
|  -r  |  실행중인 JOB만 출력  |
|  -s  |  중지된 JOB만 출력  |

이렇게 5가지의 명령어가 있는 것을 확인할 수 있습니다.

## 4. kill

kill 명령어는 특정 프로세스를 종료시킬 수 있는 명령어입니다.

kill 에는 2가지 옵션이 존재하며, 이는 각각 -9 강제 종료, -15 정상 종료의 의미를 가지고 있습니다.
사용방법은 kill -9 PID  or kill -15 PID 와 같은 형태로 사용 가능합니다.

<img width="440" alt="kill" src="https://github.com/user-attachments/assets/308ba9cd-1384-4b95-ab49-8693877b0bcf" />

ping 8.8.8.8 & 명령어를 통해 백그라운드에 ping이 실행되도록 한 상태에서, ping의 PID가 676이어서, 이미지에서 빨간색으로 표시에 둔 것과 같이, kill -9 676을 입력해주면 ping 프로세스가 종료되는 걸 확인할 수 있습니다.


