# Git이란?   

## 시작하며

안녕하세요. 멋쟁이사자처럼 충북대학교 6기 운영진 최우열이라고 합니다.

앞으로 세션시간에 매주 사용할 Git! 뭔지도 모르고 따라하시기 보단

**'아 이런거구나!'** 라고 알고 사용하시면 좋을 것 같다는 생각이 들어 여러분에 지식에 조금이나마 기여해보고자 몇 자 적어보기로 했습니다.

기억에 의존해서 찾아보며 적는거라 빠진 설명이 있을 수도 있습니당 :)

더 궁금하신게 있다면

구글에 **Git**에 대하여 검색하면 이 문서보다 훨~씬 많은 정보들이 넘치고 넘치니 검색해서 찾아봐주시면 감사하겠습니다. 

----

### Git 

**소스코드의 효율성을 위한 형상관리도구**

소스코드 수정내용이 커밋(Commit)단위로 관리됩니다.

1.  패치 형식으로 배포할 수 있기 때문에 프로그램 개발의 변동 과정을 체계적으로 관리할수있습니다.
2.  지난시점의 소스코드로 체크아웃 할 수있습니다.
3.  소스코드 주고 받기가 필요 없고, 같은 파일이 여러 명이 동시에 작업하는 것과 같은 병렬 개발이 가능해집니다. 
4.  새로운 기능을 추가하고자 개발하는 경우, 브랜치(Branch)를 통해 나눠서 만들어 본 뒤 본 프로그램에 합치는 병합(Merge)방식으로 개발이 가능합니다.

조금더 알아보시기 쉽게이미지를 하나 보여드리겠습니다.

![깃이미지](http://pismute.github.io/whygitisbetter/images/local-remote.png)

복잡해보이시죠? 요약하자면 다음과 같습니다.



"작업한 내용을 **스테이지**(Stage)에 올려서 **로컬 저장소**(Local Repository)에 **커밋**(Commit)하고, 이를 **푸쉬**(Push)해서 **원격 저장소**(Remote Repository)에 보낸다"



용어들이 익숙하지 않은 여러분을 위해 더 친절히 하나 하나 설명드리겠습니다!

본격적인 작업 시작전 Git에 관련된 용어들을 알아봅시다!

------

### 저장소(Repository)

소스코드가 저장되어 있는 여러개의 브랜치(Branch)들이 모여 있는 디스크상의 물리적 공간을 의미합니다. 흔히 Git 사용자들은 Repository를 줄여 Repo라고 말하기도 합니다. 

여기서 저장소는 로컬 저장소(Local Repository)와 원격 저장소(Remote Repository)로 나뉩니다.

- 원격 저장소(Remote Repository): 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소입니다. 


- 로컬 저장소(Local Repository): 내 PC에 파일이 저장되는 개인 전용 저장소입니다.

  ​

이에 대해선 사용법을 안내하며 더 자세히 후술하겠습니다!

------

### 체크아웃(Checkout)

작업한 내용이 올라가는 임시 저장 영역입니다. 

이 영역을 이용하여 작업한 내용 중 커밋에 반영할 파일만 선별하여 커밋을 수행할 수 있습니다.

------

### 커밋 (Commit)

작업한 내용을 로컬 저장소에 저장하는 과정입니다. 

각각의 커밋은 **의미 있는 변경 단위**이고, 변경에 대한 설명을 커밋 로그로 남깁니다. 대개 하나의 커밋은 '검색 기능 추가', '보안 취약점 수정'과 같이 하나의 주제로 묶을 수 있는 변경 단위가 됩니다.

------

### 푸시(Push)

로컬 저장소의 내용 중 원격 저장소에 반영되지 않은 커밋을 원격 저장소로 보내는 과정입니다. 

----

### 풀(Pull)

**푸시와 반대되는 개념**으로써, 원격 저장소에 있는 내용 중 로컬 저장소에 반영되지 않은 내용을 가져와 로컬 저장소에 저장하는 과정을 의미합니다. 이를 통해 다른 팀원이 변경하고 푸시한 내용을 로컬 저장소로 가져올 수 있습니다.

----

### 브랜치(Branch)

커밋을 단위로 구분된 **소스코드의 타임라인**에서 분기하여 새로운 커밋을 쌓을 수 있는 가지를 만드는 행위, 혹은 그 가지를 브랜치라고 합니다.

아마 세션동안 저희는 쓸 일이 없지 않을까 싶습니다..ㅎㅎ

![브랜치다옹](https://backlog.com/git-tutorial/kr/img/post/stepup/capture_stepup1_1_1.png)

​                                                           *출처:https://backlog.com/git-tutorial*

그래도 혹시 몰라 한가지를 짚고 넘어가고가 합니다. 

위에서 잠시 언급한 소스코드 타임라인에서 브랜치 중 개발의 주축이 되는 가장 위에 있는 브랜치를 **마스터 브랜치**(Master Branch)라고합니다. 모든 브랜치는 마스터 브랜치에서 분기되어 최종적으로 다시 마스터 브랜치에 병합(Merge)되며 개발이 진행됩니다.  

브랜치를 항상 마스터 브랜치에서 해야 하는 것은 아닙니다. 브랜치에서 또 브랜치를 할 수 있습니다.

위 그림을 보시면 **A**를 마스터 브랜치라 보신다면 조금 이해가 쉬우실 지도 모르겠네요!

----

### 병합(Merge)

브랜치와 반대되는 개념으로, 하나의 브랜치를 다른 브랜치와 합치는 과정을 의미합니다.  

두 개의 브랜치를 합쳐서 하나의 브랜치로 만드는 3-Way Merge가 모든 병합 작업의 기본이 됩니다. 

병합의 대상이 되는 두 브랜치는 주종관계가 성립하며, 따라서 'A 브랜치와 B 브랜치를 병합한다'라는 말은 모호한 표현입니다.. 

 **'A 브랜치를 B 브랜치에 병합'** 하는 작업과 **'B 브랜치를 A 브랜치에 병합'** 하는 작업은 **서로 다른 작업**입니다.

----

### Git 관련 웹 기반 솔루션

앞서 말씀드린 원격 저장소(Remote Repository)를 효율적으로 관리하는 방법은 웹 기반의 Git 솔루션을 사용하는 방법이 있습니다.

솔루션에서는 원격 저장소 관리 뿐만이 아닌 이슈,머지 요청,팀원,위키 등의 프로젝트 관리 기능을 함께 제공하고 있습니다. 웹 기반이기 때문에 브라우저만 있다면 쉽게 접근이 가능하므로 여러 작업을 수월하게 진행 할 수 있습니다.

이러한 솔루션의 대표적인 예로 **GitHub**와 **GitLab**을 들 수 있겠네요!

둘의 차이성은 폐쇄성입니다. 

GitHub는 오픈소스 프로젝트에서 많이 사용되며,

GitLab은 기업체 등의 조직에서 인트라넷에 설치하며 많이 사용하고 있습니다.

----

### 뭐가 뭔지 모르시겠죠?

Git은 공부해야 될 대상이 아닌 앞으로 여러분이 개발을 하며 활용해야 할 도구로써의 성격이 크기 때문에 아마 이거 무슨 명령어를 써야되지? 하시면서 구글링을 하실 경우가 많으실 것 같다는 생각이 듭니다.

서론에서 말씀드렸다시피 앞으로 계속 사용할 예정인 도구로써 입문하시는 분들께 간단한 배경지식을 소개시켜드리고자 작성하게 되었습니다. 

직접 프로젝트를 만들고, 개발해가며 써보고 부딪히면서 Git이라는 친구를 천천히 익히는 편이 좋다고 생각해요! 

자, 그럼 다음은 실전입니다. 앞으로 작업을 하며 저희가 사용하게 될 Git의 명령어를 알려드리겠습니다!

----

### Git 시작!

이번 목표는 나만의 Github 페이지 만들기입니다.

과정은 이렇습니다

- 새로운 로컬 저장소를 만들고

- 로컬저장소와 원격저장소를 연결하고

- 내가 로컬에서 작업한 파일을 Commit하고

- 원격 저장소로 Push하기

  ​

우선 저희는 원격 저장소로 **GitHub**를 사용할건데요, https://www.github.com/ 에 가입하시고 돌아와주세요! 



이제 정말 본격적으로 시작해보겠습니다.

https://c9.io에 로그인하고 워크스페이스를 하나 만들어볼까요?

저는 html5로 새로운 워크스페이스를 생성했습니다! 

![c9_화면](http://cfile21.uf.tistory.com/image/9947783A5AC7AF9A01C551)

​                   *아는 지식을 최대한 활용하여 html과 css를 예쁘게 꾸며봅시다! (전 귀찮아서 안꾸밈ㅋ)*

아래에 붉은색 네모로 테두리를 해놓은 곳이 bash 혹은 terminal이라 불리는 곳입니다.

이곳에서 git에 관한 명령어를 사용합니다. 따라해봅시다.

----

#### 로컬 저장소 생성하기

```
git init
```

**로컬에 빈 Git 저장소를 생성하는 명령어**입니다. 이 명령을 입력하면 현재 디렉토리에 .git 디렉토리가 생성되고, 기본 환경설정이 저장됩니다.

----

혹시나 궁금해하실분들을 위한 설명!

" .git 디렉토리가 생성되었다고 하는데 왼쪽에 보이지 않아요~ "

리눅스 환경에서 디렉토리 이름 앞에 '.' 이 붙으면 숨김파일입니다. 일반적으로 보이지 않습니다.

만약 보시고 싶다면

`ls -a`  명령어를 사용하시면 확인 하실 수 있습니다.

터미널창을 깨끗하게 만들고 싶으시다면 `clear` 를 써주세요! 

이 문서에서는 **더 이상 리눅스 명령어를  설명하지 않겠습니당** :) 궁금하시다면 개인적으로 질문질문

----

#### 원격 저장소 주소 추가하기

init 명령어를 통해 생성한 로컬 저장소에는 원격 저장소에 대한 정보가 없으므로 Push나 Pull과 같은 명령을 사용할 수 없습니다. 다음 명령을 통해 원격 저장소의 주소 정보를 입력하면 원격 저장소와 연동이 가능합니다.

`git remote add {원격 저장소 별칭} {원격 저장소 주소}`

하지만 저희는 아직 원격저장소 주소에 대해 아는바가 없습니다.

아까 만든 github에 로그인해 보겠습니다.

![커몬커몬](http://cfile26.uf.tistory.com/image/99416E3A5AC7AF990268CD)

저는 이미 가입이 되어있어서 초기화면이 기억이 나지 않습니다.  (죄송합니다 ㅠ)

이런 화면이 보이신다면 **New repository** 버튼을 누르셔서 새로운 저장소를 생성해주시면 되고,

제 기억이 맞다면 새로 아이디를 만드신 뒤 로그인하시면 대문짝만하게 

**Start Project** 버튼이 있던 것으로 기억하고 있습니다. 그 버튼을 통해 repository를 생성해줍니다.

![정상정상](http://cfile1.uf.tistory.com/image/99417A3A5AC7AF9A0282DE)

​                                                     *정상적으로 들어왔다면 이 화면이 보입니다.*

Repository name을 `본인의 유저명.github.io`  으로 생성해줍시다.  

Github는 page라는 기능을 제공하고 있습니다. 본인의 개인 Page를 만들어 서비스 할 수 있는 기능으로 참 재미있는 것은 Github답게 git으로 page를 생성하고 관리할 수 있다는 점입니다. 

여러분이 만드신 repository는 여러분의 프로필 페이지로 운영됩니다. 그래서 여러분의 유저아이디명을 사용하는 것이고, 위와 같이 계정당 유저명.github.io 로 생성한 단 하나의 repository만 page로 운용이 가능합니다.

 **Create repository를 해줍시다.**

![주소복사주소복사!](http://cfile27.uf.tistory.com/image/9947813A5AC7AF9B013FA4)

​                                                                          *다들 이런 화면 나왔죠?*

 여기서 붉은색 테두리 친 곳이 여러분이 Github를 통해 생성한 원격 저장소(Remote repository)의 주소입니다. **복사해둡시다!**

거의 다 왔습니다!

----

#### 원격 저장소 추가하기 (이어서)

이전 문단에 서술한 것 처럼

`git remote add {원격 저장소 별칭} {원격 저장소 주소}`

의 명령어를 통해 원격 저장소의 주소 정보를 입력하여 연동이 가능합니다.

저의 경우의 예시를 보여드리겠습니다.

`git remote add origin https://github.com/Choiwooyeol/Choiwooyeol.github.io.git`

https://github.com/Choiwooyeol/Choiwooyeol.github.io.git의 주소를 갖는 원격저장소를 'origin'이라는 별칭으로 등록하는 명령어입니다.

----

#### 커밋(Commit) 하기

이제 로컬 저장소에 있는 여러분의 파일들을 커밋(Commit)해 보도록 하겠습니다.

그 이전에 문서를 따라오셨다면 html의 파일의 이름이 hello-world.html 일텐데요!

이름을 **index.html로 변경** 해줍시다. 원래 웹에서 처음보이는 화면은 index인겁니다. 외우세여 (^오^) 



다음으로 여러분이 커밋하고자 하는 파일들을 지정해 줘야 합니다. 

`git add {파일명} ` 명령어를 통해 지정이 가능합니다.

그 이전에 `git status` 를 사용해보겠습니다. 보통 파일이 상태를 확인하기 위하여 사용합니다.

아마 붉은색 글씨가 나올텐데 **정상**입니다. 아직 파일이 스테이지에 등록되어있지 않았기 떄문입니다.



![Commit_status](https://git-scm.com/book/en/v2/images/lifecycle.png)

​                                                             *이 그림이 도움이 되길 바랍니다.*

위의 그림은 Commit에 대한 Status를 보여줍니다. 언젠가 이 그림의 상태가 이해가 되실때가 올거라고 생각합니다 ㅎㅎ 지금은 그다지 중요하지 않아요!



이제 파일을 추가해보겠습니다.

저희는 `git add .`  명령어를 사용해 보도록 해보겠습니다.

`.`은 **현재 디렉토리를 의미**하며 현재 디렉토리에 있는 모든 파일을 추가하겠다는 의미입니다.



`git commit -m "Usage Message"` 명령을 통해 로컬 저장소에 커밋이 가능합니다!

이중 `"Usage Message"` 의 큰 따옴표 안에는 커밋하고자 하는 메세지를 자유롭게 적어주시면 됩니다.

하지만 위에 말씀 드렸다시피 커밋하는 경우는 중요한 변경점이 있을 경우로, 저희는 첫번째 커밋이니

`git commit -m "First commit"` 으로 명령어를 작성해 보겠습니다!

성공하셨다면 

`2 files changed, 88 imsertions(+) create mod 100644 readme.mdcreate mode 100644 index.html`

과 같은 로그가 쫘라락 올라가실거고, 그렇다면 성공입니다!

----

#### 푸시(Push)하기

정말 마지막입니다!

`git push -u {원격저장소별칭} {브랜치이름}` 명령어를 통해 push 할 수 있습니다!

여기서 -u옵션은 향후에 수정된 내용을 push 혹은 pull하기 쉽게 할 수 있도록 하는 옵션입니다.

`git push -u origin master` 명령어를 사용해 봅시다!



![푸시푸시베이베](http://cfile4.uf.tistory.com/image/99E7864C5AC7BEA919E863)

​                                                                                        *성공!*

명령어를 쓰면 GitHub의 Username과 Password를 요구합니다. 아까 가입하신대로 입력해주시면

**성공입니다!**

이제 확인하러 github에 아까 만들었던 repository로 가봅시다!

![오진짜올라가네](http://cfile30.uf.tistory.com/image/99E8A14C5AC7BEA8199AE7)

​                                                   *워크스페이스에 있던 파일들이 원격저장소에 올라갔다.*

성공적으로 하고자했던 바를 다 이뤘습니다. 추카추카

http://choiwooyeol.github.io 와 같이 자신이 만들었던 repository이름의 주소로 들어가봅시다.

![잘뜨네](http://cfile5.uf.tistory.com/image/9924884D5AC7C0E81BCB18)

​                                                                            *우오오오 쩐다!!!*         



----

### 마치며

정말 간단한 예제와 함께 Git의 개념 그리고 사용법을 익혀보았습니다.

정말 일부만 맛봤으니 앞으로도 자주자주 써보며 익숙해지도록 합시다!

개발에 뜻이 있으시다면 앞으로 여러분의 Github 계정은 여러분의 개발자로써의 얼굴이 될 것이라고 생각합니다. 저도 참 많이 듣는 말인데 참 힘드네요 ㅎㅎㅎ 

매일 씻는 얼굴처럼 예쁘게 가꿔주세여 :) 

모자란 글 읽어주셔서 감사합니다. 충북대 멋사 화이팅

