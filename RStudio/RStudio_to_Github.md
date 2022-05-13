## RStudio_to_Github
- By: Sunjeong Bae, 배선정
- Date made: May 11st 2022
- Background: During AD Acpuncture microbiome dysbiosis project<br/><br/>

RStudio 작업 및 R code를 Github로 연동시키는 방법들에 대하여 정리한 글입니다.<br/>
모든 작업은 Mac OS를 기반으로 진행되었습니다.<br/>
추후 @박지한 이 Windows OS를 기반으로 작성해주길 기대합니다.<br/>

### Make Github-RStudio Repository
다양한 방법이 있지만 다음과 같은 단계로 진행하였습니다.<br/>

#### 1. Github에서 새로운 Repository 생성, 언어는 R로 선택. <br/>
  Right corner 의 circle 모양 본인 profile 클릭시 your repository 클릭 <br/>
  new repository 선택 <br/>
  repository name은 나중에 change하기 힘들기 때문에 simple 하고 직관적인 것으로 설정하는 것이 좋음<br/>
  이후 생성된 repository 홈페이지 오른쪽에 초록색 code 클릭하면 주소 확인할 수 있음 <br/>
  SSH로 (HTTPS도 될거 같긴 한데 시도해보지 않음) 주소 copy하여 준비<br/>
  <img width="422" alt="Screen Shot 2022-05-11 at 3 10 56 PM" src="https://user-images.githubusercontent.com/102775904/167780616-f72efa99-6270-4b5a-97ec-e670530519be.png">

  <br/>
  
#### 2. RStudio에서 연동 Project 만들어 열기<br/>
  RStudio 열기 <br/>
  Left corner 에 투명한 정육면체 + 가 Creat a new project임. 이것 클릭! <br/>
  아래와 같은 것이 뜨는데 세번쨰의 Cersion Control 클릭 <br/>
  <img width="547" alt="Screen Shot 2022-05-11 at 3 06 40 PM" src="https://user-images.githubusercontent.com/102775904/167780120-dfc2df44-334a-472f-a916-6e442d9ceb34.png"><br/>
  Git 클릭<br/>
  Repository URL에 아까 copy 한 ssh address 입력<br/>
  자동으로 directory name 설정 될 것임 <br/>
  원하는 위치를 선택해준 다음 Creat Project <br/>

#### 3. RStudio에 git token 연동하기
  Git token 이란 git 외부에서 내가 접속했을때 이게 나임을 알려주는 것. <br/>
  사전에 만들어서 저장해놓아야함. 꼭!!! 바로 저장!!!!!! never get to see it again (I sent it through my email) <br/>
  원래는 RStudio에서 ID+PW 를 지원했는데 이제 no more supported. <br/>
  So 이 token을 RStudio에 저장하는 과정이 필요함. <br/>
  R console에서 다음과 같은 과정을 진행하면 됨 <br/>
  
~~~R~~~
install.packages("gitcreds")
library(gitcreds)
gitcreds_set()
~~~~~~~
  이렇게 치면 token을 입력하는 란이 뜨니까 복사해놨던 것 입력ㄲ.<br/>
        이 과정은 없어도 RStudio 우측 하단의 작업 공간에서 바로 불러올 수 있다!
  
  
  
#### 4. R code Github에 commit & push 하기
  R code 생성 및 편집은 same. 문제는 이렇게 내 컴퓨터에서 저장한 것을 git에 반영하는 것! <br/>
  이를 이해하려면 git에 대한 기본 이해가 되어있어야 함. 여기[https://rateye.tistory.com/1916] 에서 직관적으로 잘 설명해주고 있음 <br/>
  무튼 기본적으로는 
  - pull을 통해 현재 main or wanted branch 상태를 그대로 가져온 후
  - 작업을 진행하고 내컴퓨터에 저장하고
  - commit을 통해 git에 올릴 수 있는 하나의 상태로 만들고
  - push를 통해 실제 git에 반영시키는 것<br/><br/>
  다른 과정들은 큰 문제가 없는데 push에서 충돌이 나는 경우가 있다.<br/>
  branch 설정 상의 문제인 것 같은데. main branch를 이용해서? <br/>
  사실 잘 모르겠고 어차피 몇명 작업 안하는 것이니까 주 사용자는 force 해주면 되기는 하는거 같다....<br/>
  Commit 후에 RStudio에서 Console 말고 Terminal 을 열고<br/> 
~~~~~
$ git push origin +main
~~~~~~~
  하면 호로록 된다.

## 끝!


