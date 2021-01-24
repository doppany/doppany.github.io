# Git cherry-pick

작업 해야하는 브랜치가 아니라 체크아웃된 브랜치에 실수로 커밋한 경험이 한번쯤은 있을것이라 생각합니다. 커밋 되돌리기(revert나 reset)도 필요하겠지만, 당장 해당 커밋을 가져와서 PR을 만들어야하는 상황이라면 당연히 cherry pick 부터 검색하셨을거라 생각됩니다. 저 또한 매번 검색하는 **cherry pick** 하는 방법을 정리하겠습니다.
> 사실 cherry pick은 다양한 이유로 사용됩니다. 매번 쓰는 기능이 아니니, cherry pick하는 시점에는 항상 실수를 하지않으려고 또다시 검색해서 확인하게 되죠. (내얘기)

## 사용법

**특정 커밋 하나를 가져올 때**
```
git cherry-pick commitHash
```
*예) git cherry-pick 1234abc*

**커밋 두 개 이상 가져올 때**
```
git cherry-pick commitHash1 commitHash2 commitHash3 ...
```
*예) git cherry-pick 1234abc 2345bcd 3456cde ...*

> 여기서 commitHash는 가져오고싶은 commit의 hash값입니다.


## 옵션
cherry pick 했는데 conflict이 발생한다면 --continue 또는 --abort 옵션을 사용할 수 있습니다.
#### -- continue: 컨플릭 해결 후
```
git add <path> // 컨플릭 해결 후 staging에 코드를 올림
git cherry-pick --continue // 체리픽 계속 진행
```
### -- abort: 체리픽 이전으로 돌아가고 싶을 때
```
git cherry-pick --abort
```
### -- edit: 커밋메시지 수정하고 싶을 때
```
git cherry-pick --edit
```