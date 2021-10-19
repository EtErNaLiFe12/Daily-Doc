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






