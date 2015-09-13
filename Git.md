# Git #
## 뭐하는 놈인가? ##
- 버전 관리 도구
- Linus Torvalds가 만듦
- 거부할 수 없는 [대세](https://www.google.com/trends/explore#q=%2Fm%2F012ct9%2C%20%2Fm%2F05vqwg%2C%20%2Fm%2F08441_&cmpt=q&tz=Etc%2FGMT-9)

## Commit ##
~~~
mkdir gitTest
cd gitTest
git init
git status
echo "Hello, World" > README.md
git status
git add .
git status
git commit -m "Add README.md"
git status
git log  
~~~

## Branch ##
~~~
git branch myBranch
git checkout myBranch 
~~~
- 한번에 -> git checkout -b
- 지울 때 -> git branch -d

## Reset ##
~~~
rm README.md
ls
git status
git reset --hard HEAD
~~~

## Merge ##
~~~
echo "\nBye, World\nfrom myBranch" >> README.md
git add .
git commit -am "Update README.md from myBranch"
git log

git checkout master
git log
echo "\nBye, World\nfrom master" >> README.md
git add .
git commit -am "Update README.md from master"

git merge myBranch
git status
~~~

## Conflict Resolution ##
- emacs -> ediff
- vim -> vimdiff
- 아니면 그냥 충돌난 파일을 직접 수정해도 됨

~~~
cat .git/config
git config merge.tool vimdiff
git config merge.conflictstyle diff3
git config mergetool.prompt false
cat .git/config
git mergetool
~~~
- 두번째 줄을 "Bye, World from mergetool!"로 수정
~~~
cat ~/.gitconfig (gitconfig는 홈 디렉토리에서 설정도 된다, 우선순위는 찾아보기)
echo "[core]\n\teditor = vimdiff" >> ~/.gitconfig
echo "[alias]\n\tlg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit" >> ~/.gitconfig
cat ~/.gitconfig
git commit밋
git status
rm README.md.orig (git add로 추가하지 않으면 git이 추적하지 않고 커밋되지도 않는다)
git lg
~~~
- 충돌이 없는 경우 알아서 똑똑하게 해준다.

## Diff ##
~~~
git diff HEAD\^1 (zsh에서는 \ 넣어줘야하는데 bash면 그럴 필요 없음)
git diff HEAD\^2 
git diff HEAD~1
git diff HEAD~2
git log 
git lg
git diff ~~~ README.md (파일 하나)
git diff --stat [커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]
~~~
- http://stackoverflow.com/questions/2221658/whats-the-difference-between-head-and-head-in-git

## Show ##
~~~
git show [커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]
~~~

## Range ##
~~~
git log [커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]..[커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]
git diff [커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]..[커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]
git show [커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]..[커밋 고유해시값, HEAD 어쩌구, 브랜치 이름 등]
~~~

## Github, Pull, Push ##
- 새로운 리포지토리 생성
- 이름이 디렉토리 이름과 같을 필요는 없음 "myGithubRepository"
- "…or push an existing repository from the command line"를 따라하기
- README.md 클릭
- newline이 이상하게 보인다.. 수정하자!
- 간단하게 엔터를 하나 더 넣어주고 웹에서 바로 커밋
~~~
git branch -a
echo "\n\nRandom Text" >> README.md 
git add . 
git commit
git push origin
git pull origin (pull = fetch && merge)
git push origin
~~~
- 여기서는 머지할 때 충돌이 일어나지 않았다!
~~~
git blame README.md
~~~

## .gitignore ##
~~~
git clone https://github.com/github/gitignore
echo "*.gitignore" > .gitignore
git rm -r --cached .
git add .
git status
~~~

## 이런 것들도 가능 ##
- 커밋에 태그붙이기
- 특정 유저가 한 커밋 로그 보기
- 브랜치 전체를 가져오지 않고 특정 커밋만 가져오기
- 한 파일의 일부만 커밋하기 (hunk 단위)
- git rebase
- git stash
- pull/push 등 사용할 때 아이디 비밀번호 없이 https://help.github.com/articles/generating-ssh-keys/
- github fork / pull request
  - 토발즈의 언급 https://github.com/torvalds/linux/pull/17#issuecomment-5654674

## 마치며 ##
- 굉장히 많이 쓰이는 도구, 자료도 많다
- 에디터의 플러그인도 잘 되있다 (vim-fugitive / emacs-magit 등)
- 이런게 있으면 좋겠다 싶으면 구글링
- 깃허브의 많은 오픈소스 프로젝트들을 보고 어떤 식으로 돌아가는지 구경
  - https://github.com/rust-lang/rust/pulls
- [git-up](https://github.com/aanand/git-up)
## Useful links ##
- http://rogerdudler.github.io/git-guide/
- https://try.github.io/
- https://git-scm.com/book/en/v2
- http://git-scm.com/docs/gittutorial
- https://github.com/git-game/git-game
- http://pcottle.github.io/learnGitBranching/
- https://help.github.com/index.html
