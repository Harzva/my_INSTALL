  ``` 
  [core]
  2         repositoryformatversion = 0
  3         filemode = true
  4         bare = false
  5         logallrefupdates = true
  6 [remote "origin"]
  7         url = https://harzva:ashzh10086@gitee.com/harzva/harzvatool.git
  8         fetch = +refs/heads/*:refs/remotes/origin/*
  9 [remote "gitee"]
 10         url = https://harzva:ashzh10086@gitee.com/harzva/harzvatool.git
 11         fetch = +refs/heads/*:refs/remotes/gitee/*
 12 [branch "master"]
 13         remote = gitee
 14         merge = refs/heads/master
```
vscode免密上传,cd .git/config
