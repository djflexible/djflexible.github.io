---
layout: blog
title:  "Github - 기초"
date:   2016-01-25
categories: blog
image: /images/blog/github_img.png
---
github의 가장 기초인 로컬 컴퓨터에서 github로 파일을 올립니다.
[Nolboo's Blog][Nolboo's Blog] 님의 블로그를 참고하면 github의 전반적인 구조를 이해할 수 있습니다. 여기서는 간단히 요약하여 설명합니다.

1. Git 다운로드
2. Repository 생성
3. 로컬 컴퓨터와 github 계정 연동하기
순서로 진행됩니다.

# 1. Git 다운로드
로컬 컴퓨터에서 온라인 상의 github 계정과 연동하기 위해 git을 다운로드 합니다.

window 8을 기준으로 작성하였습니다.
[git 윈도우 다운로드][git 윈도우 다운로드] 에서 64-bit Git for Windows Setup 을 다운로드 합니다. v2.7.1 (2016-02-06 기준)
![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic1.png)

설치를 위해 긍정의 Next를 누릅니다. git을 다운로드 받은 위치는 C:\Program Files\Git 로 합니다.

# 2. Repository 생성
이제 본인의 github 계정으로 갑니다. New repository를 눌러 새로운 repository를 생성합니다.
![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic2.png)

아래의 그림과 같이 Repository name을 myproject로 합니다.

private 할 경우 공개 수준을 정할수 있지만 이용료를 내야합니다. 여기서는 public으로 합니다.

Initialize this repository with a README 를 체크하여 초기 README.md 파일을 생성합니다. README.md는 보통 프로젝트에 관해 설명하는 텍스트 파일입니다.

나머지는 별다른 설정 변경 없이 repository를 만듭니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic3.png)

첫번째 repository를 생성했습니다!!!

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic4.png)

# 3. 로컬 컴퓨터와 github 계정 연동하기

github 계정에 올릴 파일을 로컬 컴퓨터에서 만듭니다. git을 설치한 위치 C:\Program Files\Git 에 가서 git-bash.exe를 실행합니다. 아래와 같은 이런 모양 입니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic5.png)

git-bash를 실행한 후 아래 명령어를 입력하여 자신의 github 계정을 로그인 합니다. 물론 "  " 안은 본인의 정보입니다.

	git config --global user.name "dongdongalcohol"
	git config --global user.email "djflexible@naver.com"

로그인 할 경우 아래와 같이 아무런 상태메시지가 뜨지 않습니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic6.png)


아래 명령어를 입력하여 로컬 컴퓨터의 새로운 디렉토리를 만듭니다.

	mkdir ~/myproject
	cd ~/myproject

mkdir ~/myproject 는 최상위 단계에 myproject라는 디렉토리를 만듭니다. 편의를 위해 github 계정 repository의 이름과 동일하게 합니다.

제 컴퓨터는 C:\Users\동주\myproject 에 위치하네요

cd ~/myproject 는 myproject로 위치를 이동합니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic7.png)

아래 명령어를 입력합니다.

	git init

git init 은 로컬 컴퓨터에서 원격관리를 시작하는 것을 말합니다. 이제 git으로 시작하는 명령어를 실행할 수 있습니다. 아래와 같이 실행되면 성공!!!

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic8.png)

여기서 ls를 입력해보면 master 라고 branch가 변한 것을 알 수 있습니다.
![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic9.png)

아래 명령어를 입력하여 myproject 안에 first.txt 라는 파일을 생성합니다. C:\Users\동주\myproject 에 생성되겠죠?

	touch first.txt

아래 명령어를 입력하여 현재의 상태를 알아봅니다.

	git status

이러면 아래와 같은 메시지가 뜹니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic10.png)
위의 상태창은 현재 branch가 master이고, first.txt 파일이 아직 commit되지 않고 untracked 임을 의미합니다.

따라서 아래의 명령어를 입력하여 git에 first.txt 파일을 추가 합니다.

	git add first.txt

아래 명령어를 입력하여 commit을 실행합니다. -m 뒤는 commit할 작업내용을 의미합니다.

	git commit -m "Add first.txt"

아래와 같은 메시지가 뜨면 성공

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic11.png)

아래 명령어를 입력하여 로컬 컴퓨터와 연동할 github 계정 repository를 주소를 설정합니다.
주소의 형식은 https://github.com/username/repositoryname.git 입니다.

	git remote add origin https://github.com/dongdongalcohol/myproject.git

아래의 명령어를 입력하여 원격 저장소의 주소를 확인합니다. 이제 해당 repository 주소로 fetch와 push를 할 수 있습니다.

	git remote -v

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic12.png)

아래 명령어를 입력해 push하여 파일을 올립니다.

	git push

하지만 커맨드 창에 아래와 같은 warning 메시지가 나옵니다. 현재 branch master가 upstream branch가 아니라고 합니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic13.png)

아래 명령어를 입력해 upstream branch를 master로 설정한 후 push합니다.

	git push --set-upstream origin master

아래 창이 뜨면 username을 입력합니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic14.png)

아래 창이 뜨면 github 계정의 비밀번호를 입력합니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic15.png)

아래와 같이 커맨드창에 메시지가 뜨면 성공!!!

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic16.png)

자신의 github 계정으로 가면 first.txt가 올라간 것을 확인할 수 있습니다.

![github_basic](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_basic/github_basic17.png)

이제 github의 시작입니다!!! [demun][demun]님의 블로그로 가시면 더 많은 github 명령어가 있습니다.

[Nolboo's Blog]: https://nolboo.github.io/blog/2013/10/06/github-for-beginner/
[git 윈도우 다운로드]: https://git-scm.com/download/win
[demun]: http://demun.tistory.com/2433

