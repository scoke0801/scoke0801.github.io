---
title: Github Blog 생성 정리
author: scoke0801
date: 2022-09-14 00:00:00 +09:00
categories: [Github blog]
tags: [github, blog]
---

# Github Blog 생성 정리
공부용 목적으로 github 블로그를 만들어보려고 하니, 이미 정리된 블로그들이 많아 참고를 하면서 도전한것임에도 꽤나 어려웠네요.   
윈도우 환경에서 깃허브 블로그 생성까지의  과정을 정리하여 간단하게나마 올려두니 혹시라도 보시는 분들에게 도움이 되었으면 좋겠습니다 ㅎㅎ.. 

## 1. 필요 도구 설치
루비(Ruby)로 구현된 정적 웹사이트 빌더 프레임워크인 지킬(Jekyll)을 사용하여 깃허브 블로그를 생성할 것이므로 우선 루비와 지킬을 설치해야 합니다.

-  루비 설치
	- [링크](https://rubyinstaller.org/downloads/)
- 지킬 설치
	- 1의 과정 후 설치된 Start Command Prompt with Ruby을 실행 후 아래 명령어들을 실행하여 필요 파일들을 설치해줍니다.
	- gem install jekyll
	- gem install minima  
	- gem install bundler  
	- gem install jekyll-feed
	- gem install tzinfo-data
- 설치 확인
	- Jekyll이 정상적으로 설치가 되어 동작이 가능한지 로컬에서 명령어들을 수행하여 확인해 봅니다.(생략 가능)
	- 빈 폴더를 생성해줍니다
	- 해당 폴더에서 다음 명령어들을 수행하여 Jekyll 블로그가 게시되는 과정을 확인합니다.
	- `jekyll new ./`
	- `bundle install`
	- `bundle exec jekyll serve --trace`
		- 만약 해당 명령어를 수행하였을 때 cannot load such file -- webrick (LoadError)와 같은 에러 메세지가 나온다면 아래 명령어를 수행 후 다시 시도해주세요. 
		- `bundle add webrick`
	- 정상적으로 설치가 완료가 되고 실행이 된다면 콘솔창에 Server address: http://127.0.0.1:4000/ 메시지 등이 출력이 될 것입니다. 
	- 해당 경로를 들어가보면 성공적으로 Jekyll에 의해서 다음과 같은 모습의 로컬 블로그가 생성된 것을 확인하실 수 있습니다.  
	![image](https://user-images.githubusercontent.com/28253934/189923130-4381a2d6-8f8e-46b6-b7e7-9001f3b71638.png)
 
   
