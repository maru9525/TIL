# Git Branch

### Git branch 생성

```shell
git branch branch-name
```



### checkout  에러 발생 및 해결방법

```shell
git checkout branch-name
```

Repository에서 다른 브랜치로 checkout 하려는데 에러가 발생

```shell
error: pathspec 'feature-shoveling' did not match any file(s) known to git.
```

원인 : remote의 git 에 접속한지 오래 되어 fetch를 받지 않은 것

해결방법

```shell
git remote update
git fetch
git checkout branch-name
```



