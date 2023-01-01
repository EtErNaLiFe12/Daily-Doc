# Github 관련

## 1. master branch가 리모트의 master branch를 따라가도록 설정 하기
<!--두개 다 같음-->
git push --set-upstream origin master
git push -u origin master

## 2. cherry pick - 다른 브랜치의 커밋 가져오기

### commit 한개 가져오기

git cherry-pick <commit_hash_1>
git cherry-pick 76ae30ef

### commit 여러개 가져오기
git cherry-pick 76ae30ef 13af32cc

### conflict시 (after take an action with conflict)

git cherry-pick --continue

### cancel the cherry-pick operation

git cherry-pick --abort

### merge commit을 cherry-pick 할 시

git cherry-pick -m 1 <merge_commit_hash>

## 3. git reset 관련

git reset --hard <commit_hash_1>

## 4. 강제 push 하기

git push -f

git push -f origin <branch>

## 5. 커밋 되돌리기

<!-- n개의 커밋으로 되돌리기 -->
git reset --HEAD~1... 

<!-- 이전 커밋으로 되돌리기 -->
git reset --HEAD^ 
git reset --soft HEAD^
## 6. git commit 하나로 합치고 merge 하기
git merge --squash <branch명>

## 7. git rebase
git checkout master
git pull origin master
git checkout <branch명>
git rebase master 
-> 현재 master의 브랜치에 HEAD와 위치를 같게 하고 수정사항들은 위로 올라감.
git checkout master
git merge feature/mycontent_m --ff 

rebase시에는 항상 수정사항을 master 브랜치에 merge시 위로 올릴수가 있어서 관리하기 편함.

## 8. git fatal:Authentication failed for.... 관련 에러 해결 방법
<!-- git config list 확인 -->
git config --list
<!-- git config 초기화 하기 -->
git config --local --unset credential.helper  <!--local에서 unset하기-->
git config --global --unset credential.helper <!--global에서 unset하기-->
git config --system --unset credential.helper <!--system에서 unset하기-->

출처: https://oizys.tistory.com/64 [우당탕탕 개발] 
username / password 재입력 할 것.

## 9. ssh 
git remote add origin git@github.com-work:EtErNaLiFe12/Daily-Doc.git
git clone git@github.com-work:EtErNaLiFe12/Daily-Doc.git

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 - public access token from github

## 10. github branch
git remote update <!--원격저장소에 있는 브랜치 update-->
git branch -a <!--local 브랜치 확인-->
git branch -r <!--원격저장소의 브랜치 확인-->
git branch -d feature/xxx <!--git delete in local-->
git push origin :feature/xxx <!--git delete in remote repository-->


## 11. github remote repo connection

git init
git remote add origin https://github.com/EtErNaLiFe12/Daily-Doc


## 12. remote branch condition check

git remote show origin

<!-- 리모트 브랜치와 로컬 브랜치의 관계를 상세히 볼수 있다 -->

## 13. remote branch referred update

git remote prune origin
git remote update --prune

<!-- 리모트 브랜치의 더 이상 유효하지 않은 참조를 깨끗이 지우는 명령어 이다. -->

## 14. git branch 동기화

git fetch -p

- 사용하는 이유?
원래 내용과 바뀐 내용과의 차이를 알 수 있다 (git diff HEAD origin/master)
commit이 얼마나 됐는지 알 수 있다 (git log --decorate --all --oneline)
이런 세부 내용 확인 후 git merge origin/master 하면 git pull 상태와 같아진다. (병합까지 완료)

<!-- 로컬 저장소를 최신 정보로 갱신(리모트 저장소와 동기화)하며 자동적으로 더이상 유효하지 않은 참조를 제거한다. -->

## 15. git remote connection address

git remote -v

## 16. git ssh 키 생성

terminal open

ssh-keygen

cd ~/.ssh

<!-- public 키 확인 후 복사 -->
cat id_rsa.pub 

Github -> Setting -> SSH and GPG keys -> New SSH key

복사한 public키 붙여넣기

setting 완료


## 17. git remote origin url from ssh to https

해당 work folder내에서

open .git/config

remote.origin.url=git@github.com:finset-io/betterday-app.git 를 https 주소로 변경하면됨.
## 17. git stash in CLI

git stash 
git stash pop

git stash save {name}
git stash apply stash@{[number]} <!-- 특정 stash 꺼내기 -->
git stash drop stash@{[number]} <!-- 특정 stash 삭제하기 -->

