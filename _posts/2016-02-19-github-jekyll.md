---
layout: blog
title:  "Jekyll 소개 및 설치 - github로 만들수 있는 블로그"
date:   2016-02-19
categories: blog
image: /images/blog/jekyll_img.png
---
Jekyll에 대한 간략한 소개와 윈도우 환경에서 Jekyll을 설치해 봅니다. 사전에 github 아이디가 있고 git이 설치 되어있다는 것을 전제하고 진행됩니다.

# Jekyll 소개
Jekyll은 순수한 텍스트 파일을 사용하여 github계정으로 만들 수 있는 블로그입니다. Jekyll을 장점으로는 무료, 심플함, 정적, 블로그 지향적, 버전 관리에 충실하다는 것입니다. 여기서는 Jekyll의 설치에 중점을 두기 때문에 Jekyll을 사용하는 당위성은 다음 사이트를 참고 하시면 됩니다.

[Jekyll 한글 공식 사이트][Jekyll 한글 공식 사이트], [alphafactory 님 블로그][alphafactory], [일몰님 블로그][일몰님 블로그]

# 윈도우 상에서 Jekyll 설치하기
Mac을 이용한다면 [Jekyll 한글 공식 사이트][Jekyll 한글 공식 사이트]에 있는 방법대로 몇가지 명령어만 입력하면 Jekyll을 설치할 수 있습니다. 하지만 윈도우 환경에서 Jekyll을 설치하기 위해서는 약간의 과정이 추가됩니다. 본 글은 여러분이 쉽고 빠르게 Jekyll을 설치하기 위해 원문 [Run Jekyll on Windows][Run Jekyll on Windows]을 번역하여 설명하였습니다.


# 1.1 Ruby 설치
우선 Ruby를 설치합니다. Ruby를 다운 받기 위해 [Ruby 다운로드][Ruby 다운로드]로 이동합니다. 각자 버전에 맞는 것을 설치합니다. 글을 쓴 시각 2016년 2월 19일 기준 Ruby의 최신 버전은 2.2.4 입니다. 저는 Ruby 2.2.4(x64)를 설치합니다.

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll1.png)

여기서 주의할 점이 있는데 Jekyll은 Ruby 2.x 이상의 버전에서만 호환됩니다. 혹시 Ruby가 그 이하의 버전일 경우 살제를 하고 상위 버전을 설치해야 합니다.

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll2.png)

언어는 영어로 선택해 줍시다.

긍정의 next로 갑니다.
![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll3.png)

아래 단계에서는 Add Ruby executables to your PATH 체크박스를 체크해 줍니다. 일반적으로 프로그램 언어를 설치할때 환경변수에서 path를 추가하는 것입니다. 위치가 C:\Ruby22-x64 인것도 기억해 주세요

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll4.png)

성공!!!

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll5.png)


# 1.2 Ruby DevKit설치
다음은 Ruby DevKit를 설치합니다. [Ruby DevKit 다운로드] [Ruby DevKit 다운로드]로 가서 스크롤을 내리다 보면 Development Kit에서 For use with Ruby 2.0 and above (x64 - 64bits only)가 있습니다. 다운로드!!!

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll6.png)
위치를 C:\RubyDevKit\ 로 바꾸어 줍니다!!!

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll7.png)

시간이 좀 걸립니다. 그러하다......

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll8.png)

기다리다보면 결국 성공합니다. 그 다음 RubyDevKit을 초기화 하고 Ruby와 묶어주는 작업이 필요합니다. 커맨드 창을 띄워 아래와 같이 명령어를 입력하여 RubyDevKit으로 이동합니다.

	cd C:\RubyDevKit

아래 명령어를 입력하여 버전을 확인하고 초기화 합니다.

	ruby dk.rb init

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll9.png)

아래 명령어를 입력하여 dk.rb를 설치합니다.

	ruby dk.rb install

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll10.png)
성공!!! Ruby와 RubyDevKit 설치하였으니 이제는 Jekyll를 설치할 수 있습니다.

# 2.1 Jekyll 설치

Jekyll를 설치해 봅니다. C:\RubyDevKit 위치에서 커맨드 창을 열어 아래 명령어를 입력한 후 Jekyll을 설치합니다. 참고로 gem은 Ruby gem 페키지를 이용하기 위한 명령어 입니다.

	gem install jekyll

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll11.png)

위와 같이 다운로드가 진행됩니다. 약간의 시간이 걸리네요. 커맨드 창에서 Successfully installed라는 기분좋은 메시지가 뜹니다.

마지막으로 아래와 같은 명령어가 나오면 성공!!! 글쓴 시간 기준으로 Jekyll의 최신버전은 3.1.1 입니다.

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll12.png)

* 호환성 이슈 : Window와의 호환성 문제로 혹시나 Jekyll v1.4.3을 설치하는 일이 없도록 합니다.

하지만 아직 끝난 것이 아닙니다. Jekyll를 사용하기 위해 다음 단계로 적절한 syntax highlighters를 설정합니다.

# 3. Syntax Highlighter
Jekyll에서 Syntax Highlighter를 사용하기 위해 다음을 진행합니다. Jekyll의 새 버전인 3.0은 참고했던 [Run Jekyll on Windows][Run Jekyll on Windows]와 변경된 내용이 있습니다. Syntax Highlighter를 사용하기 위해 기존에는 Rouge와 Pygments(Pygments기반) 둘 모두를 제공했습니다. 하지만 3.0 이상인 버전부터는 Syntax Highlighter을 위해 오직 Rouge만을 제공합니다. [Jekyll 3.0 변경사항] [Jekyll 3.0] 참고.

따라서 Rouge만 설치하면 됩니다.

# 3.1 Rouge 설치
Rouge를 설치합니다. C:\RubyDevKit 위치에서 커맨드 창을 열어 아래 명령어를 입력한 후 rouge를 설치합니다.

	gem install rouge

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll13.png)

Rouge 설치 성공!!!
마지막 툴 설치를 위해 아래 명령어를 입력하여 wdm을 설치합니다.

	gem install wdm

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll14.png)

이것으로 Jekyll을 실행하기 위한 기본적인 설치를 모두 마쳤습니다~ 참고를 했던 원작자는 여기까지 온것에 대해 Take a deep breath! 라는 표현을 쓰더군요 :)

# 4.1 첫 블로그 페이지 만들기 - 로컬 컴퓨터
그러면 이제 깃허브 페이지를 띄워 봅니다. C:\RubyDevKit 위치에서 아래 명령어를 차례로 입력합니다.

	jekyll new myblog	//C:\RubyDevKit 위치에서 myblog라는 jekyll 페이지를 만듭니다.
	cd myblog	//myblog로 이동한 후
	jekyll serve	//jekyll serve를 구동합니다.

커맨드 창이 아래처럼 나오게 됩니다.

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll15.png)

로컬 컴퓨터에서 아래와 같이 접속하면 확인할 수 있습니다.

	http://localhost:4000

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll16.png)

성공!!! 작업을 할때에는 로컬 컴퓨터 공간에서 진행합니다. but 우리의 목적은 로컬 컴퓨터에서만 돌아가는 블로그가 아닌 도메인 주소가 있는 깃허브 블로그 페이지 입니다. 다음과 같이 진행합니다.

# 4.2 첫 블로그 페이지 만들기 - Github 계정과 연동
로컬 컴퓨터에 만든 Jekyll 블로그를 자신의 깃허브 계정과 연동합니다.

C:\RubyDevKit\myblog 에서 shift 마우스 오른쪽 버튼을 누른 후 Git Bash Here를 누릅니다.
우선 기존에 만들어 놨던 나의 github계정과 연동합니다.

	git config --global user.name "username"
	git config --global user.email "본인 email"


![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll17.png)


	git init	//원격관리 시작

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll18.png)


	git add *	//myblog 안에 있는 모든 내용을 추가


![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll19.png)

	git commit -m "first commit"	//첫번째 commit 합니다.


![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll20.png)

아래 명령어를 입력하여 연동할 repository를 설정합니다. 여기서 본인 계정에 myproject라는 repository가 사전에 생성되어 있어야 합니다.

	git remote add origin https://github.com/dongdongalcohol/myproject.git
	git push --set-upstream origin master

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll21.png)

이제 다 왔습니다 !!! :) github에서 무료로 주는 도메인을 받기 위해 아래와 같이 settings에 들어가 해당 repository의 이름을 myblog에서 유저아이디.github.io로 바꿉니다.

	유저아이디.github.io

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll22.png)

마지막 작업입니다 !!! 아래와 같이 _config.yml에 들어가 url을 http://유저아이디.github.io 로 바꿔 줍니다.

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll23.png)

성공!!!

![github_jekyll](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/github_jekyll/github_jekyll24.png)



[Jekyll 한글 공식 사이트] [Jekyll 한글 공식 사이트]에 가면 Jekyll의 구조와 사용법에 대한 설명이 나와있습니다. 더욱 알찬 나만의 블로그를 만들어 Boa yo

+ 추가 내용 : [Jekyll 테마][Jekyll 테마]에 가시면 Jekyll을 이용한 멋진 테마를 무료로 이용할 수 있습니다.

[Jekyll 한글 공식 사이트]: http://jekyllrb-ko.github.io/
[alphafactory]: http://www.alphafactory.co.kr/post/2013/12/08/move-to-jekyll-from-wordpress/
[일몰님 블로그]: http://ilmol.com/2015/01/%EC%9B%8C%EB%93%9C%ED%94%84%EB%A0%88%EC%8A%A4%EC%97%90%EC%84%9C%20Jekyll%EB%A1%9C%20%EB%A7%88%EC%9D%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EC%85%98.html
[Jekyll 테마]: http://jekyllthemes.org/
[Run Jekyll on Windows]: http://jekyll-windows.juthilo.com/3-syntax-highlighting/
[Ruby 다운로드]: http://rubyinstaller.org/downloads/
[Ruby DevKit 다운로드]: http://rubyinstaller.org/downloads/
[Jekyll 3.0]: https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0
