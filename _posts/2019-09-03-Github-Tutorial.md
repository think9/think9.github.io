---
layout: post
title: 깃허브 튜토리얼
subtitle: 깃허브 설치 및 bash 사용법
---

<h3>예상 소요시간 : 20분</h3>

### 깃(Git)이란?

<ul>
<li>컴퓨터 파일의 변경사항을 기록하고 버전관리를 지원해주는 소프트웨어</li>
<li>로컬 환경의 저장소(Repository)에서 파일 및 변경사항을 기록</li>
<li>변경사항 기록 시 메모를 작성하여 에러가 발생하더라도 언제 문제가 발생되었는지 손쉽게 파악이 가능</li>
<li>Github로 업로드 시 온라인 소스코드 공유 및 협업 및 토론 가능</li>
</ul>

### Git 다운로드
[다운로드 페이지](https://git-scm.com/downloads) 에서 자신의 운영체제에 맞게 다운로드

[윈도우](https://git-scm.com/download/win)

[리눅스](https://git-scm.com/download/linux)

[맥(Mac)](https://git-scm.com/download/mac)

별도의 설정없이 기본 설정대로 설치를 진행해도 무난합니다.

### Github 회원가입

[Github](https://www.github.com)에 접속 후 회원 가입 진행

![GithubHome](https://user-images.githubusercontent.com/50393277/64147595-becd9280-ce5b-11e9-8bb4-b1864ebc797c.png)

<br><br>

### Git Bash

Git 설치가 끝난 후 Git Bash를 실행하면 다음과 같은 화면이 나타납니다.

![bash1](https://user-images.githubusercontent.com/50393277/64147665-f9cfc600-ce5b-11e9-89a1-c96a44d414cb.png)

<br><br>

현재 Git에는 사용자 정보가 입력되어 있지 않는 상태입니다.

아래와 같은 명령어를 통하여 사용자 정보를 입력합니다.

```
git config --global user.name "사용자 이름"

git config --global user.email "사용자 이메일"

```

![bash2](https://user-images.githubusercontent.com/50393277/64147705-2edc1880-ce5c-11e9-8775-99256d466ffc.png)

<br><br>

명령어를 이용하여 사용자의 정보를 조회가 가능합니다.

```
git config --list
```


Git에서는 저장소(Repository)라는 공간에 파일을 저장하고 버전관리 및 변경사항을 기록합니다.

아래의 과정을 통하여 Local 환경에서 새로운 저장소 환경을 만들어봅시다.

환경을 만들기 위해서는 원하는 폴더로 이동한 후 폴더를 생성합니다.

Git Bash는 리눅스 기반으로 동작하기 때문에 리눅스와 같은 명령어로 폴더 이동 및 생성이 가능합니다.

```
cd 이동하고자 하는 폴더 명

mkdir 생성하고자 하는 폴더 명
```

위와 같은 명령어를 이용하여 저장소를 만들고자 하는 폴더로 이동한 후 새로운 폴더를 생성한 후 다음 명령어를 입력합니다.

만약, 자신이 이미 작업해놓은 폴더가 있다면 해당 폴더로 이동한 후 아래의 명령어를 실행하면 됩니다.

```
git init
```

위의 명령어를 입력하면 저장소가 생성되며 성공 메시지를 확인할 수 있습니다.

![bash3](https://user-images.githubusercontent.com/50393277/64147962-fab52780-ce5c-11e9-8cbd-57e3f540083f.png)

<br><br>

이후 현재 폴더에 위치한 내용을 Local에 위치한 Git 저장소에 업로드하는 작업을 수행하겠습니다.

```
//현재 폴더의 파일 및 디렉토리 조회
ls

//현재 폴더에 있는 모든 내용을 지정
git add *

//Commit : 변경 이력을 기록하는 명령어
//-m "message" : 변경 이력에 대한 설명을 기록
git commit -m "message"
```

![image](https://user-images.githubusercontent.com/50393277/64150216-bd539880-ce62-11e9-9496-00c217f6d108.png)

<br><br>

현재까지 과정을 완료하면 Local 환경에서 Git을 설정하고 저장소에 파일을 저장하는 과정을 마쳤습니다.

이를 온라인에서 이용하기 위해서 Github라는 사이트를 사용합니다.

이제부터는 실제로 Github로 올리는 작업을 수행해보겠습니다.

[Github](https://www.github.com) 페이지에 접속한 후 상단의 Repository 메뉴를 클릭합니다.

![github1](https://user-images.githubusercontent.com/50393277/64149692-8df05c00-ce61-11e9-87af-254d24c24d80.png)

<br><br>

우측 상단의 New 버튼을 클릭합니다.

![github2](https://user-images.githubusercontent.com/50393277/64149749-baa47380-ce61-11e9-92ca-2b5538b0dfed.png)

<br><br>

추가 메뉴에서 정보를 입력합니다.

![github3](https://user-images.githubusercontent.com/50393277/64149784-d7d94200-ce61-11e9-9b44-855befe3b897.png)

<br><br>

추가가 완료되었으면 다음과 같은 화면이 나타납니다.

이때, 저장소 주소를 복사하거나 기억합니다.

![github4](https://user-images.githubusercontent.com/50393277/64149857-09520d80-ce62-11e9-8237-effedc408c11.png)

<br><br>

아래의 명령어를 이용하여 현재 저장소에서 파일을 올릴 Github주소를 지정합니다.

```
git remote add origin (복사한 Github 주소)

//수행가능한 작업 확인
git remote -v
```

![bash4](https://user-images.githubusercontent.com/50393277/64149929-25ee4580-ce62-11e9-9e50-04cf8d42283e.png)

<br><br>

해당 명령어를 입력하면 아래와 같이 Github에 로그인하라는 메시지 창이 나타납니다.

![login](https://user-images.githubusercontent.com/50393277/64150124-88474600-ce62-11e9-8c89-e30ee926c19d.png)

<br><br>

로그인을 완료하였다면 다음의 명령어를 이용하여 지정한 주소에 위치한 Github의 Repository에 파일이 업로드됩니다.

 ```
 git push origin master
 ```
 
 ![bash5](https://user-images.githubusercontent.com/50393277/64150710-bf6a2700-ce63-11e9-81fb-ec8d8d397fc3.png)
 
<br><br>

 이후 Github 페이지에 접속한 후 해당 저장소에 접속하면 파일이 업로드 된 것을 확인할 수 있습니다.
 
 ![github5](https://user-images.githubusercontent.com/50393277/64150760-dc9ef580-ce63-11e9-94f2-255f2c72bf08.png)

<br><br>


 만약 저장소에서 있는 파일을 그대로 불러오고 싶다면 아래의 명령어를 이용하면 된다.
 
 ```
 git clone (repository address)
 ```
