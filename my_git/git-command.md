
4、git add .

5、git commit -m 

6、git push origin master（git push origin 本地分支名:refs/remotes/远程分支名）

```
git config branch.master.remote <remote origin>  
  
git config branch.master.merge refs/heads/master  

git remote remove <name>
git remote -v
git config --list
git config --global --list 
git config --local --list
git remote add github https://github.com/t-c-y/test.git
git remote add origin https://github.com/t-c-y/test.git
git remote add gitee https://github.com/t-c-y/test.git

git remote rm origin
git remote add https://github.com/Harzva/One-Shot-Object-Detection.git  origin远程地址的别名
git remote add git@gitee.com:Yourgitee_username/YourGitRepo.git
git remote add  originee https://gitee.com/harzva/One-Shot-Object-Detection.git   
git@gitee.com:harzva/One-Shot-Object-Detection.git

git remote add  https://gitee.com/harzva/One-Shot-Object-Detection.git


git config --local user.name "Harzva"
git config --local user.email  "626609967@qq.com"

git config --global user.name "Harzva"
git config --global user.email  "626609967@qq.com"
git fetch origin master

git fetch --all //只是下载代码到本地，不进行合并操作
git reset --hard origin/master  //把HEAD指向最新下载的版本
git reset --hard 目标版本号
```


```
master 是一个本地分支
origin/master是远程分支（它是名为“origin” 的远程分支的本地副本，名为“master”）
git fetch origin main
```
