# Git Study note

## revert vs reset

### reset
reset 원격지에 올리기 전에 만

e.g.)
``` git
git log
5
4
3 <-- 이 지점으로 돌아갈때 5,4 지우고
2
1
git reset "commit id" --hard
```

### revert
지점으로 돌아가고 새로운 버전 생성

gistory 실행
cmd
C:\Users\terrybyte\gitRepo>C:\Python\Python36-32\Scripts\gistory.exe

$ git branch : 현재 브랜치를 확인한다.
$ git checkout exp : 현재 브랜치를 바탕으로 exp 브랜치를 만든다
$ git checkout master : 현재 브랜치에서 master 브랜치로 체크 아웃한다.
$ git log --branches --decorate --graph
$ git log --branches --decorate --graph --oneline
$ git log master..exp
$ git log -p exp..master

terrybyte@mis-cr62-6m MINGW64 ~/gitRepo (master)
$ git checkout exp : exp를 master로 병합

terrybyte@mis-cr62-6m MINGW64 ~/gitRepo (master)
$ git branch -d exp
Deleted branch exp (was 0e0f985).

stash - 감추다, 숨겨두다
git stash --버전관리가 되는 파일만 가능하다.ㄴ
git stash list
git stash apply
git stash drop
git stash apply; git stash drop; == git stash pop;

git reset --hard 6945b65ea3165bde3d7f3eb7c03d6847f94c43e7
: 해당 커밋 시점으로 되돌아가고 해당 커밋 이후의 커밋은 삭제
현재 브랜치의 최신 커밋을 가리킴
git reset --hard ORIG_HEAD : reset 복군
git reflog

git checkout 95c1bfa01dfa26ae4f790c8fd5eb5fb75ff61b1a
git diff : index와 working copy 내용 비교

kdiff, beyond compare : git merge tool
install kdiff
git config --global merge.tool kdiff3
git config --global merge.tool bc

git mergetool

git init --bare remote : bare 작업은 불가 저장만
git init --bare remote
local$ $ git remote add origin /c/Users/terrybyte/gitStudy/remote
origin : /home/git/remote alias
git remote -v
git remote remove origin : origin remote를 제거한다.
git push
git push --set-upstream origin master 설정 시
git push == git push --set-upstream origin master 동일함

git commit -amend : 코멘트 수정

작업전/후
git pull, git push

github login by using ssh
ssh-keygen

id_rsa : private key
id_rsa.pub : public key
접속하고자 하는 원격 서버에 id_rsa.pub를 카피함.

github > setting > ssh & GPG keys
click "new ssh key"
