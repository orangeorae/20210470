# 오픈소스 sw개론 과제

## top 명령어

### top명령어는 리눅스의 프로세스를 표시하는 프로그램입니다.
윈도우의 작업관리자랑 비슷하며 리눅스를 사용하는 서버의 성능이나 현재 돌아가고 있는 상황을 볼 때 사용합니다.
1) 유닉스 계열의 시스템에서 프로세스 목록을 CPU 사용률이 높은 것부터 보여줍니다.
2) top 명령어는 시스템의 프로세스와 메모리 사용상태를 5초의 간격으로 업데이트 하여 화면에 출력합니다.
3) 어떤 프로스세가 CPU를 많이 차지하고 있는지 체크할때 실시간을 볼 수 있습니다.

top 명령어를 실행하면 

<img src="https://user-images.githubusercontent.com/106830111/171924999-d1dfd2d5-18c1-4281-a053-527ab0fc6739.png" width="600" height= "300">
사진처럼 결과가 나오게 됩니다.

top -b 옵션을 통해 순간의 정보를 확인할 수도 있으며 

top -n 2 옵션을 사용하여 top 실행 주기를 2번 반복할 수도 있습니다.

**top 명령어 실행 후 쓸 수 있는 명령어**
+ shift + p  : CPU 사용률이 높은 프로세스를 순서대로 표시합니다.
+ shift + m  : 메모리 사용률이 높은 프로세스를 순서대로 표시합니다.
+ shift + t  : 프로세스가 돌아가고 있는 시간 순서대로 표시합니다.
+ k : 프로세스 kill -k 입력후 종료할 PID 입력 singal 을 입력하라고 할 경우 kill signal인 9를 입력합니다.
+ a : 메모리 사용량에 따라 정렬합니다.
+ b : Batch 모드를 작동합니다.
+ 1 : CPU Core별로 사용량을 보여줍니다.
+ h : 도움말
+ 
이 외에도 더 많은 명령어들이 있습니다.
## ps 명령어

### ps 명령어는 현재 실행중인 프로세스 목록을 확인할 수 있습니다.

ps 명령어를 사용하여 pid, cmd 등 프로세스의 기본적인 내용을 알 수 있습니다.

<img src="https://user-images.githubusercontent.com/106830111/171929993-07a6a030-feb9-4065-8b17-9662e9d67005.png" width="600" height="300">

**ps 명령어 실행 후 쓸 수 있는 명령어**
+ ps -e : 모든 프로세스를 출력합니다.
+ ps -f : 풀 포맷으로 출력합니다.(uid,pid,ppid,TTY 등 정보를 보여줍니다.)
+ ps -l : 긴 포맷으로으로 출력합니다.(풀 포맷 + F, S,PRL등 정보를 더 보여줍니다.)
+ ps -p 1 : 프로세스 번호가 1인 프로세스를 출력합니다. 
+ ps -o : 출력 포맷을 지정합니다.
+ ps -p : 특정 PID를 지정하여 출력합니다.

이 외에도 더 많은 명령어들이 있습니다.

## ps와 top의 차이점 ##
+ ps는 ps한 시점에 proc에서 검색한 CPU 사용량을 출력합니다.
+ top은 proc에서 일정 주기로 합산해 CPU 사용율을 출력합니다.


## jobs 명령어

### jobs 명령어는 백그라운드에 실행되고 있는 프로세스나 중지된 프로세스의 목록을 출력해줍니다.

**jobs 명령어 사용 방법**

1) jobs [옵션] [job ID]

2) jobs-x command [args]

__jobs 명령어 옵션__

+ jobs -l : 프로세스 그룹 ID를 state 필드 앞에 출력
+ jobs -n : 프로세스 그룹 중에 대표 프로세스 ID를 출력
+ jobs -p : 각 프로세스 ID에 대해 한 행씩 출력

**jobs로 알 수 있는 세션의 상태 값**

|상태|설명|
|--|-----|
|Running| 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done| 작업이 완료되어 0을 반환하고 종료 했음을 의미|
|Done(code)| 작업이 정상적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped| 작업이 일시 중단|
|Stooped(SIGTSTP)| SIGTSTP 신호가 작업을 일시 중단|
|Stooped(SIGSTOP)| SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)| SIGTTIN 신호가 작업을 일시 중단|
|Stooped(SIGTTOU)| SIGTTOU 신호가 작업을 일시 중단|


## kill 명령어

### kill 명령어는 프로세스를 종료시킬때 쓰는 명령어 입니다. 
kill 명령어를 사용하여 프로세스에 시그널을 보내 원하는 작업을 하는데 쓰이기도 합니다.

**kill 명령어 사용 방법**

kill [옵션] [pid]

ex) 실행중인 특정 프로세스를 죽이고 싶다면 ps 명령어를 통해 해당 프로세스의 pid를 얻고  kill 명령어의 파라미터로 넘겨 실행중인 프로세스를 종료 시킬 수 있습니다.

__kill 명령어 옵션__

+ kill -s : [시그널 번호 or 이름] : 보낼 시그널을 지정합니다.
+ kill -l : 시그널 목록을 출력합니다.
+ kill -9 [pid] : 강제종료를 킵니다.

이외에도 kill -s SIGKILL[pid] 등 여러가지 방법이 있습니다.

## killall 명령어
killall 명령어는 프로세스 번호가 아니라 프로세스 이름으로 프로세스에게 시그널을 보냅니다.

**killall 명령어 사용 방법**

killall [옵션] [프로세스명] : SIGTERM을 해당 프로세스에게 전송

__killall 명령어 옵션__

+ killall -g : 프로세스가 속한 프로세스 그룹을 종료시킵니다.
+ killall -i : 종료전에 확인을 요구합니다.
+ killall -l : 시그널 목록을 출력합니다.
+ killall -s : [시그널 번호 or 이름] :  SIGTERM 대신 지정한 시그널로 프로세스에게 전송합니다.
+ killall -v : 시그널이 성공적으로 보내졌다면 보고합니다.
+ killall -V : 버전정보를 출력합니다.
+ killall -w : 프로세스가 종료될 때까지 대기합니다.

### vim 에디터에서 매크로 사용 방법 ###

## 매크로 저장하기 ##
-사전 조건 : [Normal /command 모드]

1) q <저장할 매크로 문자> : 매크로 기록을 시작합니다.
2) 동작을 수행한 후
3) q 로 매크로 기록을 종료합니다.

ex) -a 문자에 매크로 내용을 기록했다면 qa ->  매크로작성 -> q 를 해줍니다.

## 매크로 사용하는 법 ##

1) @<저장한 매크로 문자 > : 특정 문자에 저장한 매크로 실행
2) 반복횟수@<저장한 매크로문자> : 매크로 반복 실행
3) @@ : 마지막에 수행한 매크로 실행

## 참고 사이트 ##
[top 참고 사이트 1](https://sabarada.tistory.com/146)

[top 참고 사이트 2 ](https://bebeya.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4-top-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC-%EB%B0%8F-%EC%84%A4%EB%AA%85-%EB%8B%A8%EC%B6%95%ED%82%A4-%ED%99%95%EC%9D%B8)

[top 참고 사이트 3 ](https://blog.naver.com/dktmrorl/222635202537) 

[ps 참고 사이트 1](https://jhnyang.tistory.com/268)

[ps 참고 사이트 2](https://blog.naver.com/dktmrorl/222416977486)

[ps 참고 사이트 3](https://blog.naver.com/tmk0429/222318530824)

[jobs 참고 사이트 1](https://terms.naver.com/entry.naver?docId=4125682&cid=59321&categoryId=59321)

[jobs 참고 사이트 2](https://shaeod.tistory.com/968)

[kill 참고 사이트 1](https://codingdog.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4-kill-%EB%AA%85%EB%A0%B9%EC%96%B4-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%97%90-%EC%8B%9C%EA%B7%B8%EB%84%90%EC%9D%84-%EB%B3%B4%EB%82%B8%EB%8B%A4)

[kill 참고 사이트 2](https://121202.tistory.com/45)

[vim 에디터 매크로 사용 방법 참고 사이트 1](https://coldmater.tistory.com/226)

[vim 에디터 매크로 사용 방법 참고 사이트 2](https://clem.tistory.com/29)


