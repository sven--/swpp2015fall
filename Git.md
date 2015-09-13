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

## Useful links ##
- http://rogerdudler.github.io/git-guide/
- https://try.github.io/levels/1/challenges/21
- http://git-scm.com/docs/gittutorial
- https://github.com/git-game/git-game
- http://pcottle.github.io/learnGitBranching/
