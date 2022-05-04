[git lfs](https://git-lfs.github.com/)
---

>[github lfs storage](https://hbase.tistory.com/221)

```bash
# git lfs 세팅. 사용자 계정 당 한번이면 됨.
git lfs install

# add lfs
git lfs track "*.psd"

# track 설정 파일 버전관리 추가
git add .gitattributes
```

> [migrate import](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.1.ronn#import)
```bash
# 50MB이상 파일 lfs로 이전
git lfs migrate import --above=50MB
```

git reset
---

[gist](https://gist.github.com/qkrsogusl3/77238d4b2929fb90107c363bb3fd6048#file-git-cli-cheat-sheet-md)
[git tree visualized image](https://da-nyee.github.io/posts/git-git-reset-git-reflog/)

https://developer-ankiwoong.tistory.com/773
