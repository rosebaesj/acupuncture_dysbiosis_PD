# Found a swap file by the name "~~~~~
출처: https://dream-reverseengineer.tistory.com/entry/vivim-Found-a-swap-file-by-the-name-2가지-해결-방법 [어느 악성코드 분석가 지망생의 지식창고]\
해결 방법(1): vi/vim에서 자동으로 swap파일을 삭제하기\
Q(Quit)이나 A(Abort)를 눌러 vi/vim을 빠져나간다.\
ps를 눌러 vi나 vim이 실행 상태에 있는지 확인한다.\
만약 실행 중이라면, kill 명령을 통해 해당 프로세스를 종료한다.\
~~~~~~~~
hallym@S26-VM-N8-186:~/week07$ kill -9 12101 
[1]+ Killed vi week07-02.c
~~~~~~~~
다시 vi를 들어가게 되면, swap파일을 삭제할 수 있는 창이 뜬다. 여기서, D(Delete)를 눌러 해당 파일을 삭제한다.\
