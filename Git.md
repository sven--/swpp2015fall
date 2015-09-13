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
(한번에 -> git checkout -b)

(지울 때 -> git branch -d)

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
- 아니면 그냥 README.md를 수정해도 됨

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
git commit
git status
rm README.md.orig (git add로 추가하지 않으면 git이 추적하지 않고 커밋되지도 않는다)
git lg
~~~
- 충돌이 없는 경우 알아서 똑똑하게 해준다.


## Useful links ##
- http://rogerdudler.github.io/git-guide/
- https://try.github.io/levels/1/challenges/21
- http://git-scm.com/docs/gittutorial
- https://github.com/git-game/git-game
- http://pcottle.github.io/learnGitBranching/
