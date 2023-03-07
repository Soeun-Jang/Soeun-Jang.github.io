---
layout: post
title: "첫 Github기념! Github blog 만들어보자"
excerpt: "야호 나두 만들 수 있다"

categories: Git,Github.
tags: [Git,Github,blog,jekyll]

toc: true
toc_sticky: true

date: 2023-03-06
last_modified_at: 2023-03-06

author: Soeun-Jang
---

<git blog 만들기> - 참고 url(https://supermemi.tistory.com/145)
1. 레포지토리 생성-공개범위 : public, Read me설정-레포지토리 이름 형식 username.github.io (블로그로 접속할 도메인)-프로젝트 별로 페이지를 만들 수도 있다. 
2. 레포지토리 clone하기 (나는 Git Desktop 이용)
3. index.html 생성
4. 파일 push하여 블로그 메인 생성
5. 테마 적용을 위한 Jekyll 설치 (*Jekyll : Ruby언어로 개발한 프레임워크) 
6. Ruby가 없다면 Ruby 먼저 설치 (m1은 권환 때문에 rbenv 설치해야함), (brew 존재하지 않는 에러일 경우 참조 확인)(1) brew update     brew install rebenv ruby-build  // brew 업데이트 후 rbenv 설치(2) rbenv versions 버전 확인     rbnev install -l 설치 가능 한 ruby버전 목록 -> 최신 버전 다운, 안되면 이전 버전으로 해보기     rbnev install 3.1.3 (23.03 기준 3.2.1이 최신버전이나 error가 있어서 이전버전으로 다운(3) rbenv global 3.1.3 글로벌 버전 변경       rbenv versions로 다시 확인 하면         system     * 3.1.3 (set by /Users/jangso-eun/.rbenv/version)      jangso-eun@jangso-euns-MacBook-Air Soeun-Jang.github.io %  이렇게 3.1.3이 *로 선택되어있다면 ok(4) rbenv PATH추가하면 끝!      터미널에서   vi ~/.zschrc 입력 -> i 입력 -> [[ -d ~/.rbenv  ]] && \
           export PATH=${HOME}/.rbenv/bin:${PATH} && \
           eval "$(rbenv init -)" 코드 추가       -> esc :W -> 터미널 끄고 재접속 -> source ~/.zshrc 입력  끝 !
7. ruby 설치 후 jekyll 찐 설치 해보자 !(1)위의 고난을 해결했다면 이제  gem install bundler  gem install jekyll 입력해 지킬을 설치해보자구
8. 기존 index.html을 삭제하기 위해rm -f index.html 입력 후 제거해준다. (이렇게 하는 이유 리포지토리에 파일이 있으면 jekyll new ./ 명령이 conflict남)
9. jekyll new ./ 설치 후 push (원격저장소에 연결된 root directory에 저장해야 한다! 나는 Readme파일도 지우니 충돌해결) 
10. 터미널에서 클론한 github.io  폴더로 cd 명령으로 이동해주고 jekyll new ./
11. bundle install -> bundle exec jekyll serve(로컬서버에 지킬 띄움) -> 127서버주소가 나온다!
12. 127서버 주소에는 내가 변경한 정보가 적용된 블로그로 확인되지만 내 github.io를 띄워보면 적용되지 않은 부분이 보인다.당연함 왜냐면 Github pages에서 호스팅 되고 있기 때문 push를 해서 Github repositorie에 업로드해야 반영된다!자 127 서버는 Ctrl+c 해서 꺼주고 git add . git commit -m "커밋 메세지"git push 해주면 몇 분 이내로 반영된 내 Github blog가 뜰거임~ 

<git blog를 맥 vscode로 구현 - 에러 해결 >
1. Jekyll다운을 받기 위해  행동 : gem install bundler 명령어 입력결과 : ERROR:  While executing gem ... (Gem::FilePermissionError)You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.원인 : MacOS 시스템이 ruby를 사용하고 있기 때문에 권한 문제로 발생한 에러 메세지해결 : system ruby가 아닌 rbenv 설치하면 해결! 
2. rbenv설치 하려고 brew update 입력 시 에러행동 : brew update 명령어 입력결과 : -bash: brew: command not found원인 : m1,m2의 기본 설치 경로가 기존 인텔맥과 달라서 발생함 (환경변수) 해결 : zshrc안에 brew 경로가 향하도록 명령어 입력해줌         vi ~/.zshrc -> i를 누르고 (insert) -> brew가 설치되어 있는 경로 입력 (export HOME_BREW = "/opt/homebrew/bin") -> esc눌러 insert 끄고 :w (저장) -> 터미널 끄고 다시 터미널 재접속 -> source ~/.zshrc (이 컴퓨터에서 zshrc라는 파일 경로를 추가할게~~) -> brew (어 되네~~) -> 행복한 개발 공부 시작~~
3. 첫 게시글을 post하고 push하였는데 깃 블로그에 적용되지 않았다.검색해보니 그 때도 루트 디렉토리로 들어간 후 bundle exec jekyll serve로 서버를 켜주고 나니     Regenerating: 1 file(s) changed at 2023-03-07 09:12:43
_posts/2023-03-06-firstpost.md      이렇게 저장이 된 걸 확인할 수 있었다! 


<Homebrew delete>
터미널에 명령어 다음과 같이 입력
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"


<posts 폴더에 글 등록하기>
1. theme 설정까지 완료하였다면, 첫 글을 등록해보자!
2. post 형식은 _posts폴더>YEAR-MONTH-DAY-title.md 
3. md파일 생성 후 vi 또는 원하는 에디터로 작성
4. 파일 markdown 형식Front-Matter(머릿말)=> 위 아래 --- 써줘서 머릿말을 구분해준다..---title: "첫 블로그 글!"excerpt: 블로그 글의 요약 미리보기categories: - Blogtags:- [Blog, gitblog, jekyll] toc: truetoc_sticky: truedate: 2023-03-06last_modified_at: 2023-03-26--- 
5. Markdown Preview Enhanced확장으로 VScode설치해서 웹으로 마크다운 작성한 것을 보여줌 
