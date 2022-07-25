# HOW TO USE GIT
Git &amp; Github 설치 및 사용법
---------------------------------------------------------------------------------------
①②③④⑤⑥⑦⑧⑨⑩
### 1. 설치
① **git-scm.com** 접속하여 들어가서 git 프로그램 설치<br>
② 표준으로 설치 후 명령 프롬포트 실행<br>
③ 명령 프롬포트에서 c:\로 디레토리 변경 후 git 입력해서 설치 제대로 됐는지 확인<br>
- 이때, git 관련하여 여러 개의 명령어가 표시되면 제대로 설치되었다는 것이다.
  
---------------------------------------------------------------------------------------
### 2. 명령어/문법
- Git에는 다수의 명령어(status ,branch, add, commit, log, fetch, clone 등등)가 존재한다.
<br>
① **status** : git의 현재 상태를 알려주는 명령어<br>
사용 방법 : git status<br>
<br>
② **add** : git에 새로 추가되거나 수정된 파일 또는 폴더들을 git local 저장소에 추가하는 명령어<br>
git status 명령어를 실행시켰을 때 'untracked file'은 git에서 변경사항을 감지했으나 아직 추가하지 않았다는 의미임(아직 사진이 찍히지 않았다는 뜻)<br>
사용 방법 : git add "파일 디렉토리 경로" (여기서 add 뒤에 .을 붙이면 모든 변경사항을 추가하겠다는 의미)<br>
<br>
③ **commit** : add 명령어로 새롭게 추가한 사항들을 기록하는 명렁어(사진을 찍는다는 뜻)<br>
사용 방법 : git commit -m "기록하고 싶은 표현"<br>
특     징 : commit이 성공적으로 적용이 되면 working tree is clean 이라는 메세지가 출력된다.
<br>

git log하면 commit 내역 나옴(commit의 앞 7자리가 대표 일련번호)<br>

git add . 은 모든 변경사항을 다올리겠다는 얘기<br>
화면 높이 낮을 때는 엔터누르면 내려가고 q누르면 exit됨<br>

git reset --hard HEAD~ => 잘못쓴거 제거하는거(~모양은 몇단계를 내릴지 정하는 거임)<br>


HEAD는 커서다<br>

branch pointer = master<br>


이력이 추가될때 마다 master & head가 수정된 걸로 동시에 올라감(아래 그림처럼 실행이 됨)<br>
branch pointer는 여러개 생성이 가능(헤드만 옮기는 것으로 해결 가능)<br>



index <- master <- head<br>

            
v1 < master < head<br>
index<br>

v2 < master < head<br>
v1<br>
index <br>





다시 복구 시킬때는 로그 확인후에 해당 식별번호나 id명을 입력시켜줘야함<br>

로그 확인  : git reflog<br>
복구 명령어 : git reset --hard id명(HEAD@{2}) || git reset --hard 식별번호<br>

폴더 만들고 먼저 git init해도 됨.<br>


안전한 공간에서 실험을 하는 방법 : branch를 하나 더 만드는 방법(데모버전으로 실험하는 것) 아래 상황 참고<br>

              lab1 ->  v2 < master < head           이후 헤드(커서)를 lab쪽으로 올리고(얹히고) 성공하면 commit 후에 master에 반영<br>
                       v1<br>
                     index <br>

commit의 결과는 이렇게 됨.<br>

 head  -> lab1 ->  v3<br>
                   v2 < master <br>
                   v1<br>
                   index <br>




branch 만드는 방법 <br>
* git branch 하고 엔터 -> branch 목록이 보여짐<br>
* git branch lab1하고 엔터 -> lab1 branch 생성 (*가 있는 것은 해당 branch에 커서가 있는 거임)<br>
커서를 움직이는 명령어 : checkout<br>
* git checkout lab1 -> branch를 lab1으로 이동시킴<br>


만약 성공해서 master의 포인트를 올려서 하고 싶다면?<br>
merge 명령어 사용<br>
git merge lab1 엔터 => 병합이 되면서 master가 lab1가 병합됨<br>

만약 실험중에 master에서 버그가 생겨서 양갈래로 갈려진다면 그 위에단에 lab1이랑 합치면 됨,<br>

-------------------------------------------------------------------------------------------------------------------------------------------

### 20220704
            
![git의 구조](https://user-images.githubusercontent.com/107795925/177078245-06aecd7b-14ef-45a2-904a-3af7d6be2050.PNG)
            
git gui 누르면 gui를 조작할 수 있는 창이 뜸(gui사용시간동안은 bash에서 명령어 사용 불가)<br>
repository에서 visualize all branch history를 클릭하면 현재 상태와 히스토리가 뜸<br>
git gui & -> git bash 말고 새로운 프로세스에서 gui를 실행한다는 뜻(독립적으로 하기 때문에 bash에서 명령어 사용 가능)<br>
-> 즉, 독릭접이 프로세스를 사용하겠다는 말<br>

커서를 바꾸면 git gui에서 진한 글씨로 표시됨.<br>

lab1에서의 실험을 master로 합병시킬때는 merge 명령어 사용(master에서 변경사항 없을 때는 쉽게 merge 가능)<br>
-> 이러한 방식을 fast-foward 방식이라고 함<br>
            
![fast-foward 방식](https://user-images.githubusercontent.com/107795925/177078147-69568712-6e09-4d75-97e4-f280769341bc.PNG)

![fast-foward 방식 결과](https://user-images.githubusercontent.com/107795925/177078165-85e33694-fe8f-4c64-a23d-e9dcfa86ab18.PNG)
            
삭제 방법 : git branch -d lab1(lab1 branch포인트를 삭제하는 명령어)<br>
            
![branch 포인터 삭제 방법](https://user-images.githubusercontent.com/107795925/177078178-667a0bee-82f9-40c6-8a54-a293431cb811.PNG)
            
![branch 포인터 삭제 결과](https://user-images.githubusercontent.com/107795925/177078184-f359cc58-46df-412c-95fb-053c2e0e46e3.PNG)

중간에 branch가 갈라졌을 때는 병합을 시킬려면 master로 이동한다<br>
충돌이 날 경우에는 충돌해결-add-commit 하면 됨.<br>

![branch 갈라졌을 때](https://user-images.githubusercontent.com/107795925/177078205-28307577-df84-47a4-8586-ceba0ab07157.PNG)

![충돌(conflict 발생) 화면](https://user-images.githubusercontent.com/107795925/177078219-78a4dec7-3597-49d0-8d42-9c922d0b0023.PNG)






            
* 그냥 merge를 할 경우에는 conflict라는 충돌메세지가 나타남(에러는 아님)<br>
==== / >>>> 이런 이상한 기호는 모두 지운 후에 정리한다.<br>
            
![갈라졌을 때 최종 merge 결과](https://user-images.githubusercontent.com/107795925/177078226-669e93ce-c428-40f3-83ad-a67b11316b56.PNG)

---------------------------------------------------------------------------------------------------------


* git bash 로컬저장소의 파일들을 github 원격 저장소에 원격저장하는 방법<br>
- 공유시트에 주소 다 나와있음.

* git remote add origin https://github.com/silverstone2/my_repo.git에서 origin은 이름을 의미함
위의 명령어를 git bash에 치고 엔터<br>
이후 git remote -v를 쳐서 등록한다 그러면 두개의 주소가 나오는데 등록이 정상적으로 된거임.<br>
* git push -u origin main(main은 branch명을 적으면 됨) 바로 push 불가능
계정과 비밀번호만으로는 불가하고 인증키(토큰)을 발급받아야함.<br>
한번 발급 받으면 저장을 해놔야함(잃어버리면 삭제하고 다시 재발급 받아야함.)<br>

깃헙 본인계정 - settings - developer settings - personal access tokens를 발급받아야함<br>
new generate - 비밀번호 입력 - note 알아서 적고 Expiration은 no Expiration으로 설정<br>
그리고 밑에 repo 체크(권한은 다 체크하고 싶으면 다 체크해도 됨) 그리고 generate<br>
토큰 나오면 이 토큰을 저장해야함 한번에 저장해야함!<br>

* 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

git push -u origin main 치면 창이 하나 뜸 그때 토큰 누르고 아까 발급받은 토큰 입력<br>
토큰 정보가 맞으면 push가 진행됨.<br>
윈도우 검색 - 자격증명 관리자 - window뭐시기 자격 보면 github에 대한 자격증명있고 암호 다 젖아되어 있어서 다음에 자동으로 가능함


git remote -v : 저장된 목록 확인(연동된)

origin/master는 master보다 하나 더 ahead 되어 있다. origin/master가 master보다 하나 더 올라와 있다는 뜻.
local에는 원격저장소를 tracking하는 branch가 있다.
local과 remote가 맞춰지려면 두번 푸시를 진행해야한다.
'Your branch is up to date'문구가 나오면 끝났다는거임

최초에 add commit하고나서 하면 push를 진행하면 'Your branch is ahead of 'origin/master' by 1 commit'이라는 문구가 뜸
이러면 한번더 push를 진행해주면 된다.[스샷 push과정 참조]

집에서 할 때는 git에 저장되어 있는 상태 그대로 clone을 해줘야함. clone의 경우는 최초에 한번만 해주면 됨.
단순히 파일만 가져오는 것이 아니라 브랜치/커밋 등 모든 상태를 다 끌고 올 수가 있음.


push 코드 순서<br>
init-add-commit-remote add origin 주소-push -u origin.aster-remote -v-add-commit-status -> ahead 확인-origin master-status<br>
->up to date 확인-add-commit-status ahead-origin master-push-uptodate 확인

![push과정](https://user-images.githubusercontent.com/107795925/177121227-61fb7be3-a782-45e4-a8cf-f968a9a6041a.PNG)

![push1](https://user-images.githubusercontent.com/107795925/177121351-c9fc62f9-28e8-4665-9218-a6d6a139eeae.PNG)

![push2](https://user-images.githubusercontent.com/107795925/177121362-95c7b1d9-bcb9-4d45-9c8f-a50107753e1a.PNG)

![push3](https://user-images.githubusercontent.com/107795925/177121378-981511ae-4c6a-4aa4-bf52-1ef41d537979.PNG)

![push4](https://user-images.githubusercontent.com/107795925/177121392-17e61d5d-705b-4074-9c20-eeb79d52d6bc.PNG)

clone하는 과정 : git clone repository주소
-> 저장소의 이름대로 폴더가 복제가 됨(단지 폴더 자체만 복사될뿐임 그러므로 git bash를 안쪽으로 들어가줘야함)
cd 폴더명 입력하고 이후 git status 하면 Your branch is up to date with 'origin/master'. 요러한 문구가 나옴.
이후부터는 commit을 그냥 내려받기만 하면 됨 -> 이는 fetch라고 부름.

![clone 구조](https://user-images.githubusercontent.com/107795925/177121408-905f36af-4b4a-415c-b42b-f44264cee2c5.PNG)

![clone1](https://user-images.githubusercontent.com/107795925/177121431-c2dcc114-867b-4f20-8d17-21a7e95b3efe.PNG)

fetch를 진행하면 오리진 마스터가 마스터보다 어헤드가 됨. 그러면 merge를 통해서 합병시켜버리면 됨
원격저장소에서 가장 최신으로 받는 건 fetch+merge 방법 / 원격저장소로 보내는 건 push

fetch진행방법 : git fetch origin
이후 git status에서 보면 어헤드되어있음. 그래서 git merge origin/master로 merge를 진행해준다.

![Fetch를 진행했을 때의 구조](https://user-images.githubusercontent.com/107795925/177121464-cb11310f-57ff-4e46-a7b9-742f3f1fdfe8.PNG)

똑같은 곳을 수정 안하면 자동 머지가 됨.

![fetch 이후 merge진행하면 master가 제일 위로 올라옴](https://user-images.githubusercontent.com/107795925/177121527-83d16afe-2410-483a-9e42-2d882c3308f6.PNG)


그러면 파란 글자가 써져있는 글이 뜨는데 이건 bash 편집기 이고
뜨면 :wq쓰고 엔터하면 됨. 그러면 merge가 됨.

![최종구조(fetch 후 merge)](https://user-images.githubusercontent.com/107795925/177121487-12e1d833-f070-4681-a733-768acc1320af.PNG)

-----------------------------------------------------------------------------------------------------------------------------

git reflog 는 git에서 행한 작업들에 대한 로그를 모두 보여줌(reflog = reference log)

일반적으로 취소를 할때는 git reset 명령어를 사용하는게 맞지만 사용하면 안될 경우도 있다 그 경우는 commit한 것을 이미 github에 올린상태라면 reset하는걸 고려해보아야함(올린걸 clone해서 다른 작업하고 있으면 대참사발생) 이럴 경우에는 취소하는 이력을 따로 commit해주면 된다.

한 줄에 로그 표시하고 싶으면 git log --oneline

reset은 hard, soft, mixed 3가지의 옵션이 있다! 일부 수정만 할거면 mixed untracked file까지 강하게 되돌릴거면 hard 좀 약하게 할거면 soft
