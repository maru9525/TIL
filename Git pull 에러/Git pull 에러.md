### Git pull 에러

`Your local changes to the following files would be overwritten by merge`



해결방법

1. git stash

- 현재 디렉토리의 파일을 임시로 백업하고 깨끗한 상태로 돌린다.

- 버전관리 되는 대상 파일들을 임시저장 해둔다고 보면 된다.

  1. 해당 명령어를 통해 현재 staging 영역에 있는 파일의 변경사항을 스택에 넣어둔다.

  ```shell
  git stash
  ```

  2. master에서 pull하거나 , git checkout 등 원격 저장소에서 내 로컬 브랜치로 변경사항을 적용한다.

  ```shell
  git pull origin master
  ```

  3. 변경 사항을 적용하고, 스택에서 제거한다.

  ```shell
  git shash pop
  ```

  이후 정상적으로 git pull이 가능한 것을 볼 수 있다.



2. git add

- git add를 통해 해당 파일을 staging 영역에 저장하고 git pull 자겅ㅂ을 해도 해당 오류는 해결 가능하다.

```shell
git status
On branch master Your branch is behind 'origin/master' by 29 commits, and can be fast-forwarded. 
(use "git pull" to update your local branch) 

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory) modified: 소스~ 

no changes added to commit (use "git add" and/or "git commit -a")

```

