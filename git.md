# Git

## Config

`git config --global [user.](http://user.name)email "eshinhw@gmail.com"`

`git config --global [user.name](http://user.name) "eshinhw"`

## Initialization

`git init`

## Record

![Screen Shot 2022-08-27 at 11.34.41 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae153fdf-c226-426c-898b-649114fc63c2/Screen_Shot_2022-08-27_at_11.34.41_AM.png)

- 커밋하고 싶은 파일을 고르는 작업: `git add [file_name]`
- 커밋하는 작업: `git commit -m [commit_message]`
- 기록이 필요한 파일들만 추가할 것.
- 이미지 파일 등과 같이 기록이 필요없는 파일들은 굳이 추가할 필요는 없음.
- `git add .` 작업 폴더의 모든 파일들을 staging.
- `git status`
- `git log --all --oneline`
- 커밋은 간단한 기능같은 것을 구현했을 때 체크 포인트 형식으로 실행.

## Difference

- `git diff`: 작업 전 파일과 변경 후 파일과의 차이점 비교. (쓰레기 같음…)
- `git difftool [commit_id]` : 비쥬얼 적으로 더 보기 편한 방식의 차이점 비교.
- 요즘은 확장 툴들이 잘 나와서 굳이 터미널 상에서 보지 않아도 됨!

## Branch 개념

- 파일 복사본을 만들어 거기에 먼저 코드를 짜보면 실수해도 괜찮다!
- 프로젝트 복사본 또는 커밋의 복사본
- `git branch [branch_name]`: 현재 소스 코드의 사본 파일 생성
- `git switch [branch_name]`
- `git checkout -b [branch_name]`
- `git log --oneline --all --graph`
- `HEAD` : current location
- `git merge [branch_name]` at `main`
- `git branch -d [branch_name]` : delete a branch
- `git branch -D [branch_name]` : delete a branch forecefully?
- `git branch -M [new_branch_name]`

## Merge

### 3-way

각 브랜치에 신규 commit이 있는 경우

![Screen Shot 2022-08-27 at 12.59.26 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/753e99a0-d2ca-4f80-bbf3-ef5079b0326d/Screen_Shot_2022-08-27_at_12.59.26_PM.png)

### fast-forward

기준 브랜치에 신규 커밋이 없는 경우 

![Screen Shot 2022-08-27 at 1.00.50 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/358f621b-d659-4c49-b21b-6dd3ecb9cb09/Screen_Shot_2022-08-27_at_1.00.50_PM.png)

만약 자동으로 fast-forward 되는 것을 원하지 않는 경우, `git merge --no-ff [branch_name]` 옵션 이용.

강제로 3-way merge 발생.

`merge` 말고 다른 방식으로 브랜치들을 합칠 수 있음!

### rebase

![Screen Shot 2022-08-27 at 1.05.24 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2a20b574-a0d9-42a4-bac9-a3420759f1ab/Screen_Shot_2022-08-27_at_1.05.24_PM.png)

브랜치의 시작점을 `commit2` 에서 `commit3` 로 옮김. 그 후 `fast-foward merge` 사용하여 합친다.

`fast-forward merge` 는 기준 브랜치에 커밋이 일어난 경우 불가능한데, `rebase` 후에 `merge` 할 경우 `fast-forward` 사용 가능.

`rebase` 사용 이유…?

- 브랜치 없이도 코드 잘짜는 고수같음 ㅋㅋㅋ
- `3-way merge`는 나중에 `git log` 출력시 히스토리가 복잡해짐.
- 간단한 브랜치 같은 경우는 `rebase` 사용시 히스토리가 더 간결해짐. 브랜치 커밋을 깔끔하게 이어 붙일 수 있음.
- 단점은 merge conflict 잦음.

![Screen Shot 2022-08-27 at 1.10.57 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14c173a4-3c14-41ef-a598-53a1b7e37f9f/Screen_Shot_2022-08-27_at_1.10.57_PM.png)

`git merge` 남발 시 히스토리가 더러워짐!!

### squash and merge

- `git merge --squash [new_branch]`
    
    ![Screen Shot 2022-08-27 at 1.14.01 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e19ec40-6fb0-4bca-8cea-cb64d0f0866b/Screen_Shot_2022-08-27_at_1.14.01_PM.png)
    
    merge 되기 전 브랜치의 자잘한 커밋들은 메인 브랜치에 합쳐질 시 보여지지 않음.
    
    `git log`를 깔끔하게 유지하고 싶을 경우 사용
    

## Revert, Reset, Restore!

- 파일 단위의 복구
    - `git restore [file_name]` 현재 커밋의 최초 시점으로 파일 복구
    - `git restore --source [commit_id] [file_name]` 과거 커밋의 시점으로 파일 복구
    - `git restore --staged [file_name]` 스테이징에 올려놓은 파일 제거
- 커밋 단위의 복구
    - 깃에서는 과거 커밋 자체를 삭제하는 것은 불가능하지만 과거 커밋에서 작업한 것을 제거하는 커밋은 생성 가능
    - `git revert [commit_id1] [commit_id2] ...` 여러개의 커밋 아이디 입력 가능
    - `git revert HEAD` 방금 생성한 최근 커밋 취소 가능
    - `merge commit` 도 취소 가능
- 과거로 돌아가기
    - `git reset --hard [commit_id]`
    - 극단적인 삭제이기 때문에 협업시에는 사용 금지!
    - 짧은 과거로 되돌아갈때는 가능하지만 왠만하면 사용금지
    - `git reset --soft [commit_id]` 리셋이지만 변동사항을 삭제하지 않고 스테이징 해놓기
    - `git reset --mixed [commit_id]` 리셋이지만 변동 사항을 삭제하지 않고 언스테이징 해놓기

## Remote Repository

`git push -u [remote_repo_address] [local_repo]`

`git remote add origin [github_url]`

`git push` 할때 `-u` 추가하면 주소를 기억하라는 뜻

## git clone, git pull

- 원격저장소에 새로운게 생기면 `git push` 못함
- `git pull`: 원격 저장소의 내용을 로컬 저장소로 가져와 합치기
- `git pull` 이 `git push` 보다 선행되어야 한다.
- `git pull origin [branch_name]`
- `git pull` = `git fetch` + `git merge`
- `git fetch` 원격 저장소의 신규 커밋 가져오기
- `git merge` 가져온 신규 커밋들을 내 브랜치에 합치기
- GitHub Pull Request시, 3가지 머지 방법 있음.
    - 3-way merge (normal)
    - squash and merge (for clean git log)
    - rebase and merge (small branch)

## git stash

`git stash list`

최근 커밋과의 차이점을 전부 보관해줌.

한가지 예외는 스테이징을 해놓지않은 새로운 파일은 스태싱이 안될수도 있다.

`git stash save [memo]`

`git stash pop` 가장 최근에 보관된 스태쉬가 불러와진다.

`git stash drop 번호`

`git stash clear` 전부 삭제

## git flow / trunk-based branch strategy

프로젝트가 커지고 사람이 많아져도 branch 와 머지를 깔끔하게 하고 싶다면, GitFlow / Github Flow / Trunk-based / Gitlab Flow 등의 전략들을 적용해 볼 수 있다.

가장 유명한 전략 중 하나는 GitFlow by Vincent Driessen.

### GitFlow

1. main: release 에서 만족스러울 경우 메인 브랜치로 합쳐지고 유저에게 배포
2. develop: 신기능들이 제작되고 먼저 합쳐지는 곳.
3. feature: 각 기능들은 feature 브랜치에서 먼저 제작되고 develop 브랜치로 코드 리뷰 후 합쳐진다. (feature/guild, feature/friend…)
4. release: develop 에서 바로 메인으로 가기 보다는 release 브랜치에서 전체적인 테스팅을 진행한다.
5. hotfix: 메인 브랜치에서 바로 고쳐야하는 수정 사안들은 hotfix로 고칠 수 있다.

![Screen Shot 2022-08-28 at 6.44.24 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae8245b4-23f5-4da4-86d8-1bf8b2601371/Screen_Shot_2022-08-28_at_6.44.24_AM.png)

### Trunk-based development

![Screen Shot 2022-08-28 at 6.46.02 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/369380fd-0921-4221-8331-3fc010b60233/Screen_Shot_2022-08-28_at_6.46.02_AM.png)

브랜치 구조가 간단하고 쉬워서 소스 코드 관리가 쉽다.

메인에 있는 소스 코드를 유저들에게 바로 배포하기 때문에 많은 테스트가 필요하고 자주 해주어야 한다.

테스트 자동화, 배포 자동화

안정화된 프로젝트에서 많이 사용되는 전략.

[GitHub - pvdlg/conventional-commit-types: List of conventional commit types with emoji](https://github.com/pvdlg/conventional-commit-types)

# **Git Basics**

## **Typical Git Usage**

1. `git checkout -b DEV-101`: branch off main and create your feature
2. `git add --all`: add the untracked files to your next commit
3. `git commit -m "commit msg"`: create your commit
4. `git push`: push the commit

Systematically divide up the works with team projects backend vs frontend vs database etc

`git checkout -b BRANCH_NAME` creates a new branch and checks out the new branch.

`git branch BRANCH_NAME` creates a new branch but leaves you on the same branch.

## **Merging vs. Rebasing**

There are two methods for bringing code in from other branches into your own

- merging: combines branches together into a commit
- rebasing: modify, mutate and move commits on your branch

### **Merging**

`git merge <branch>`

creates a commit which combines the tip of the master branch (HEAD) and the tip of the feature branch into one commit

- this commit is referred to as a "merge commit"
- the merge commit becomes the new HEAD after the merge is complete.

### **Rebasing**

moves things around, the first commit of feature branch is placed sequentially after the tip of the branch you're rebasing onto.

compares the latest version of main branch and the latest version of feature branch and move them into one linear structure without extra commit. (like linked list)

We want to rebase feature branch INTO main branch not the other way around.

- no extra commit merging the two
- partially rewrites the git history by creating brand new commits for each commit in the master branch
- requires extra step to merge: **rebase feature branch on master, then merge**

## **How do we undo a commit?**

- **reverting**: undoing your changes
- **resetting**: changes the state of head
- **restore**: restore your changes
- **stash**: store your changes for later

## **Pull Request**

- After pushing your changes into a branch, you create a pull request from your branch into the develop branch.
- Automated checks will run against it informing you of any bugs/errors.
- It can be then reviewed by one or more engineers, where they can provide comments on how to improve it.

## **Commit Type for Meaningful Commit Messages**

Must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- **test**: Adding missing tests or correcting existing tests
