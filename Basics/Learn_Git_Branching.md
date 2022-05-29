# Learn_Git_Branching
by Sunjeong Bae
date 2022 May 15
from https://learngitbranching.js.org/?locale=ko

## Git commands 명령어
- commit \
git 저장소에 '스냅샷'을 기록하는 것. 디렉토리를 붙여넣는 것과 유사\
commit은 가볍게 유지되기 위한 것으로 이전-이후 의 변경 내역 (delta) 을 저장하는 것. \
저장소를 복제하는 경우 모든 delta를 풀어내가게 됨.\
~~~~~~~~~
git commit
~~~~~~~~~~~

- branch \
branch는 특정 커밋에 대한 reference. 브랜치를 자주 만들 것이 권장됨.\
작업을 커다란 브랜치로 만들기보다 작게 나누는 것이 좋음.\
일단 branch는 커밋과 그 부모 커밋을 포함하는 작업내역\
~~~~~~~~~
git branch newbranchname
~~~~~~~~~~~

- checkout
branch를 만든다고 바로 거기로 가는게 아니고 그 branch로 내가 이동해야함\
그렇게 branch를 옮기는 명령어가 checkout\
그 후에 commit하면 newbranch 가 기록됨
~~~~~~~~~
git checkout newbranchname
~~~~~~~~~~~
- merge\
지금 위치한 brach로 다른 branch를 흡수하는 것\
A에 B를 흡수한다면 아래와 같이\
~~~~~~~~~
git checkout Abranch
git merge Bbranch
~~~~~~~~~~~
근데 여기까지가 아니라 후에 진짜 완전히 하나로 합쳐버리려면\
~~~~~~~~~
git checkout Abranch
git merge Bbranch 
git checkout Bbranch
git merge Abranch
~~~~~~~~~~~

- rebase\
merge와 유사하지만 한줄로 정리하고자하는 경우. 보기 좋음\
merge는 내가 있는 곳으로 다른 것을 불러오는 것이라면 \
rebase는 내가 다른곳 다음으로 이동하는 느낌\
A로 B를 연결하고자 할 때
~~~~~~~~~
git checkout Bbranch
git rebase Abranch
~~~~~~~~~~~
근데 여기까지가 아니라 후에 진짜 완전히 하나로 합쳐버리려면\
~~~~~~~~~
git checkout Bbranch
git rebase Abranch
git checkout Abranch
git rebase Bbranch
~~~~~~~~~~~
이정도면 기본은 다 했다!!!

## 추가 공부
- head\
현재 checkout 된 커밋. 현재 작업중인 commit. 작업 트리에서 가장 최근의 커밋.\
일반적으로 branch 이름을 가르킴. \
그런데  branch에서 분리할수도 있음. 이건 아얘 commit을 가르키는 상태가 되는 것임.\
근데 commit 이름을 찾기 어려울수도 있음 그럴때는 상대참조를 할 수 있음\
~~~~~~~~~
git checkout main^ #main의 부모
git checkout main^^ #main의 조부모
git checkout main HEAD~4 #main에서 4개 위
~~~~~~~~~
이를 이용해서 이전 commit으로 다시 branch를 옮길 수 있음\
근데 이건 force해야함
~~~~~~~~~ 
git branch -f main HEAD~3 
~~~~~~~~~
혹은 내 현재 head 위치로 branch를 강제 이동 시키고 싶으면\
~~~~~~~~~ 
git branch -f main
~~~~~~~~~

## 작업 되돌리기 Reset revert
- reset\
내가 실행한 멍청한 작업을 되돌리는 경우\
아얘 이전 커밋으로 branch가 이동함\
git branch -f main HEAD~1 이랑 같다고 볼 수 있음\
- revert \
남이 작업을 한 경우 되돌려버려 기록을 지워서는 안됨\
따라서 이전상태와 똑같은 상태를 만들어 커밋하는 것으로 생각해야함\

~~~~~~~~~ 
git reset HEAD~1
git revert HEAD #혹은 HEAD 대신 branch 이름을 적어도 됨
~~~~~~~~~

## 원하는 commit만 선택적으로 반영하여 넣기
~~~~~~~~~~~~
git cherry-pick C2 C4
~~~~~~~~~
그런데 만약 원하는 커밋을 모른다면?
~~~~~~~~~~~~
git rebase -i HEAD~4
~~~~~~~~~~~~
이렇게하면 이전 4개 HEAD를 대화형(-i)으로 확인가능


## not something we can merge
해결방법
https://bongbongreview.tistory.com/57

그래도 
did not match any file(s) known to git
라고 뜨는 경우는 완전 신규 브랜치라서 그럼
https://gofnrk.tistory.com/95
그런 경우에는 
~~~~~~~~~~~~~~~
git remote update
git fetch
~~~~~~~~~~~~~~
한 후에 진행 해주면 된다
~~~~~~~~~~~~~~~~~
git checkout new-branch
git checkout main
git merge new-branch
~~~~~~~~~~~~~~~~~
