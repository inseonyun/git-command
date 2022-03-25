## 개요
+ ### GitHub를 관리하면서 가끔씩 사용하는 명령어의 경우 까먹고 Search 하는 일이 종종 있어 공부도 할 겸 정리하게 됐다.

## 목차
+ ### [Git 사용자 정보 등록](#git-사용자-정보-등록-1)
+ ### [원격 저장소 내려 받기](#클라우드-저장소-원격-저장소-내려받기)
+ ### [변경 사항 반영](#변경-사항-반영-1)
+ ### [원격 저장소의 변경 사항 내려 받기](#클라우드-저장소-원격-저장소-의-변경-사항-내려-받기)


## 기본 명렁어
+ ## Git 사용자 정보 등록
  <pre>
    git config --global user.name 이름 입력
    git config --global user.email Git 이메일 주소 입력
    
    <예시>
    git config --global user.name inseonyun
    git config --global user.email inseonyun@mail.com
  </pre>
  
<br> </br>

+ ## 클라우드 저장소 (원격 저장소) 내려받기
  + ### 여러가지 방법이 있겠지만 일반 사용자가 많이 사용하는 명령어는 clone 일 것 같다. <br> 이 외에도 SSH를 통해 다운 받은 경험이 있으니 혹시 몰라 정리했다.
    ### Clone
    <pre>
      git clone 'git Https 주소'
    
      예시 -> git clone https://github.com/inseonyun/git-command.git
    </pre>
    
    ### SSH
    #### 1. SSH 키 생성
    #### ❗ 주의 ❗ 무턱대고 생성하면 기존 SSH 키가 사라질 수 있으니 꼭 존재하는지 확인 요망
    <pre>
      cd ~/.ssh
      ssh-keygen -t rsa -b 4096 -C "본인 깃허브 이메일 주소"
    </pre>
    #### 위 명령어를 실행하면 아래와 같이 키를 저장하고자 하는 위치, 비밀번호 설정 여부를 물어본다. (특별한 사항 없을 시 디폴트(엔터))
     <pre>
      Generating public/private rsa key pair.
      Enter file in which to save the key (/home/user/.ssh/id_rsa): 
    </pre>
    
    <pre>
      Enter passphrase (empty for no passphrase):
      Enter same passphrase again:
    </pre>
    
    #### 이후 *.pub 이라는 파일의 공개키의 내용을 복사하여, 본인의 GitHub 계정 SSH Key에 등록을 해준다.
    
    #### 2. GitHub에 SSH 키 등록
    ![image](https://user-images.githubusercontent.com/84364741/160071627-945e79c8-22f1-4e51-9f79-9d2ad656ee8f.png)
    ![image](https://user-images.githubusercontent.com/84364741/160071831-2aa8b3e5-b2cf-4c92-ba55-c468d18c3461.png)
    ![image](https://user-images.githubusercontent.com/84364741/160071948-220d30c7-109f-4570-8f38-9f6f92c763e0.png)

    #### 3. SSH를 통해 원격 저장소 내려 받기
    <pre>
      git clone 'git SSH 주소'
    
      예시 -> git clone git@github.com:inseonyun/git-command.git
    </pre>

<br> </br>

+ ## 변경 사항 반영
  + ### 회사 / 조직 내 Repository가 아닌 경우 일반적으로 변경 사항 반영은 Add - Commit - Push 순으로 진행 된다.
    #### Add
    <pre>
      git add .     // 모든 변경 사항을 add 함
    </pre>
    #### Commit
    <pre>
      git commit -m "여기에 메시지 작성"    // commit 메시지 작성
    </pre>
    #### Push
    <pre>
      git push     // 모든 변경 사항을 commit message 주제로 push 함
    </pre>
    
<br> </br>
    
+ ## 클라우드 저장소 (원격 저장소) 의 변경 사항 내려 받기
  + ### clone 명령어와 다른 점이 있다면 clone은 소스 코드를 처음 받을 때 받는다는 점이다. <br> 여기서 다룰 fetch / pull 명령어의 경우 원격 저장소를 내려받은 로컬 저장소에서 원격 저장소의 변경 사항을 내려받는 명령어이다.
    ### Fetch
      + #### fetch는 원격 저장소에서의 변경 사항을 내려 받기 전에 확인 할 수 있게 해준다.
      <pre>
        git fetch
      </pre>
      
      + #### 위 명령어를 실행하면, 아래 명령어를 통해 변경사항이 있는 브렌치 정보를 확인 할 수 있다.
      <pre>
        git branch -r               // 변경 사항이 있는 브렌치 확인
        git checkout '브렌치 이름'   // 변경 사항 있는 브렌치로 이동
      </pre>
      
      + #### Q. 그럼 위 변경 사항을 내 로컬 저장소에 반영하고 싶다면??
      + #### A. pull 명령어를 실행하면 된다.
      
    ### Pull
    + #### pull 명령어의 경우 'fetch + checkout branch + 내려받기' 를 pull이란 명령어 한 번에 모두 수행하는 동작이다.<br> 난 그래서 웬만하면 pull 명령어를 쓴다....개인 프젝은 당연하고, 팀, 회사, 조직 내의 협업에서 어지간 해서는 conflict가 발생할 일이 없기 때문에,,,(그래도 혹시 모르지만 conflict 해결 방법은 많기 때문에,, 굳이,,,?)
      <pre>
        git pull      // 원격 저장소의 변경 사항을 로컬 저장소에 반영함
      </pre>
