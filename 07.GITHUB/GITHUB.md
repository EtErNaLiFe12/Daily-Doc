# Github 관련

## 1. master branch가 리모트의 master branch를 따라가도록 설정 하기

git push --set-upstream origin master

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

## git commit 하나로 합치고 merge 하기
git merge --squash <branch명>

## git rebase
git checkout master
git pull origin master
git checkout <branch명>
git rebase master 
-> 현재 master의 브랜치에 HEAD와 위치를 같게 하고 수정사항들은 위로 올라감.
git checkout master
git merge feature/mycontent_m --ff 

rebase시에는 항상 수정사항을 master 브랜치에 merge시 위로 올릴수가 있어서 관리하기 편함.

## git fatal:Authentication failed for.... 관련 에러 해결 방법
<!-- git config list 확인 -->
git config --list
<!-- git config 초기화 하기 -->
git config --local --unset credential.helper  <!--local에서 unset하기-->
git config --global --unset credential.helper <!--global에서 unset하기-->
git config --system --unset credential.helper <!--system에서 unset하기-->

출처: https://oizys.tistory.com/64 [우당탕탕 개발] 
username / password 재입력 할 것.

## ssh 
git remote add origin git@github.com-work:EtErNaLiFe12/Daily-Doc.git
git clone git@github.com-work:EtErNaLiFe12/Daily-Doc.git

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 - public access token from github

## github branch
git remote update <!--원격저장소에 있는 브랜치 가져오기-->
git branch -a
git branch -r
git branch -d feature/mycontent_m <!--git delete in local-->
git push origin :feature/mycontent_m <!--git delete in remote repository-->

