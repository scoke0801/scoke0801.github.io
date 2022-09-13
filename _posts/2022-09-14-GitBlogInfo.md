---
title: GitBlog
author: scoke0801
date: 2022-09-14 00:00:00 +09:00
categories: [Github blog]
tags: [Github, blog]
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
  ![](https://user-images.githubusercontent.com/28253934/189923130-4381a2d6-8f8e-46b6-b7e7-9001f3b71638.png)
  
## 2. 깃허브 저장소 만들기
깃허브에서 <계정이름>.github.io 형식으로 저장소를 생성해줍니다.
![](https://user-images.githubusercontent.com/28253934/189920168-58680b36-74a3-4eff-88b3-8dfc674767a6.png)  

생성된 저장소 경로를 원하는 폴더 경로에 clone하여주세요.

## 3.  Jekyll 테마 적용 ( Chirpy )
아래의 사이트들에서 마음에 드는 테마를 골라 적용할 수 있습니다.
- https://jekyll-themes.com/free/
- http://jekyllthemes.org/
- http://themes.jekyllrc.org/

저는 http://jekyllthemes.org/themes/jekyll-theme-chirpy/ 요 링크의 테마가 깔끔하니 이뻐보여 선택하여 적용하였습니다. 

![](https://user-images.githubusercontent.com/28253934/189919639-1852673f-11da-4243-8664-e2ae0cdbb2b3.png)
Download를 눌러 테마를 다운받아줍니다.
테마를 적용하기 위하여 불필요한 파일들의 삭제가 필요합니다.
다행히도 이러한 절차가 tools/init.sh 파일에 작성이 되어있기에 해당 파일을 실행함으로써 간단히 해결해줍시다.

- 압축해제된 루트 폴더에서 마우스 좌클릭하여 Git Bash Here 를 클릭합니다.
- 다음 명령어를 실행하여 위의 파일이 실행되도록 합니다.
- `sh tools/init.sh`
- 리눅스 환경이 아닌 윈도우 환경에서 작업할 것이기에 플랫폼 처리를 위하여 다음 명령어를 실행해주세요. 
- `bundle lock --add-platform x86_64-linux`
- .gitignore파일 하단에 Gemfile.lock 파일을 추가해주세요

## 3-1 '_config.yml' 수정

현재 블로그의 기본 스킨은 테마 개발자의 정보를 기반으로 작성된 디폴트 값이기 때문에  
'_config.yml'파일에서 아래의 내용들을 사용자 정보에 맞게 수정해주어야 합니다.
- lang :: en -> kor
- timezone :: Asia/Shanghai -> Asia/Seoul
- title 
- tagline
- url
- github
- Social.Name ~ Social.links
- avatar
- theme_mode

또한 추가적으로 구글 광고에 관련된 내용들이 있으나 해당 부분은 제가 적용을 하지 않아 생략합니다...

'_config.yml'파일의 수정까지 모두 완료가 되었다면 github블로그 생성 및 테마 적용까지의 준비가 모두 완료되었습니다.
현재 설정한 테마의 스킨 정보가 정상적으로 설정이 되었는 지 로컬 블로그에서 우선 확인해보고 싶은 경우  
1. 필요 도구 설치에서 처럼 아래 명령어들을 수행하여 확인 가능합니다.
- `bundle install`
- `bundle exec jekyll serve --trace`

## 3-2 블로그 배포
마지막으로 현재까지 작업한 파일들을 깃에 커밋하여 깃허브 블로그가 생성되는 것을 확인합시다.  
정상적으로 모두 배포가 되었다면 https://사용자계정.github.io 주소로 접속하였을 때 아래와 같은 화면이 보이게 됩니다. (게시글은 없는 게 정상입니다)   
![](https://user-images.githubusercontent.com/28253934/189927580-06297038-e88c-4d98-8585-5ae233c97fb3.png)
  
  ##  4. 추가 사항
비교적 최신 글을 참고하더라도 Chirpy 테마를 적용하고 setting ->  Github Pages에서 브랜치를 변경해주어야 한다는 내용이 많았습니다.  
그런데 내부적으로 구조가 변경이 된 것인지는 모르겠지만 저의 경우 해당 브랜치가 생성이 되지 않으나 정상적으로 블로그 생성 및 게시글이 작성이 되는 것을 확인하였습니다.   
![](https://user-images.githubusercontent.com/28253934/189928031-6683fec6-30ca-4936-b847-c6879063611d.png)  

### 참고 블로그
> (Jekyll이란?) https://cheershennah.tistory.com/214  
> (Jekyll테마 적용) https://seong6496.tistory.com/267  
