# Git Study note

## revert vs reset

### reset
reset 원격지에 올리기 전에 만

```
git log
5
4
3 <-- 이 지점으로 돌아갈때 5,4 지우고
2
1
git reset --hard commit_id
```

#### git reset --hard 6945b65ea3165bde3d7f3eb7c03d6847f94c43e7
: 해당 커밋 시점으로 되돌아가고 해당 커밋 이후의 커밋은 삭제
현재 브랜치의 최신 커밋을 가리킴
```
$ git reset --hard ORIG_HEAD : reset rollback
$ git reflog
$ git checkout 95c1bfa01dfa26ae4f790c8fd5eb5fb75ff61b1a
```

### revert
커밋 지점으로 돌아가고 새로운 버전 생성

### branch
$ git branch : 현재 브랜치를 확인한다.

## checkout
$ git checkout exp : 현재 브랜치를 바탕으로 exp 브랜치를 만듦

```
$ git checkout master : 현재 브랜치에서 master 브랜치로 체크 아웃
```

## log
```
$ git log --branches --decorate --graph
$ git log --branches --decorate --graph --oneline
$ git log master..exp
$ git log -p exp..master
```

## merge
~/gitRepo (master) $ git merge exp : exp를 master로 병합

## branch delete
~/gitRepo (master) $ git branch -d exp
Deleted branch exp (was 0e0f985)

## stash
stash - 감추다, 숨겨두다
```
$ git stash --버전관리가 되는 파일만 가능하다.
$ git stash list
$ git stash apply
$ git stash drop
$ git stash apply; git stash drop; == git stash pop;
```

## git diff
: index와 working copy 내용 비교
kdiff, beyond compare : git merge tool;
install kdiff
```
$ git config --global merge.tool kdiff3
$ git config --global merge.tool bc
```

## git mergetool

## remote
```
$ git init --bare remote : bare 작업은 불가 저장만
$ git init --bare remote
local$ $ git remote add origin /c/Users/terrybyte/gitStudy/remote
origin : /home/git/remote alias
$ git remote -v
$ git remote remove origin : origin remote를 제거한다.
$ git push
$ git push --set-upstream origin master 설정 시
$ git push == git push --set-upstream origin master 동일함
$ git commit -amend : 코멘트 수정
$ git pull, git push : 작업 전/후
```

## github login by using ssh
$ ssh-keygen 개인키,공개키 생성
```
id_rsa : private key
id_rsa.pub : public key
접속하고자 하는 원격 서버에 id_rsa.pub를 카피
```

## github > setting > ssh & GPG keys
: "new ssh key"

## git clone
```
$ git clone git@github.com:lepetit80/Git-Bash.md.git Git-Bash.md
```

## make remote git-server
: 서버에 원격 저장소를 만들고 ssh를 이용하여 버전 관리
```
~server $ git init --bare remote
: 원격 저장소 생성
local $ git remote add orgin ssh://git@192.168.1.100/home/git/git-remote/
: 로컬 저장소를 원격 저장소를 연결. "/" 를 붙여야 함.
local $ git remote -v
local $ git push
local $ git push --set-upstream origin master

office $ git clone ssh://git@192.168.1.100/home/git/git-remote/ git-office
: 원격 저장소 복제
```

## #caution push & pull
```
: push 전, pull하여 원격지와 로컬을 동기화(충돌 처리 등)한 후 push
```
