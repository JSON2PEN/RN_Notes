

- **git init** :在本地创建仓库,创建出.git文件
- **git status**:查看任务栈中的任务;
- **git diff**  file:文件版本的不同之处;
- **git add file**:将文件添加到任务栈中;
- **git log** :处理文件的的日志;
- **git log --pretty=oneline**;输出简洁的日志;
- **git commit -m "提交日志"**;提交到版本库,并添加提交日志;
- **cat file**;查看文件内容;
- **git reset --hard HEAD^**;回退到上一个版本库版本;
- **git reset --hard HEAD~10**;回退到是10个版本前
- **git reset --hard HEAD^^**;回退到两个版本前;
- **git reset --hard commitID**;回退到版本库某个提交的ID;
- **git reflog** ;查看命令历史;
- **git checkout --file**;使文件回到最近一次的git add或者Git commit;
- **git reset HEAD file**;把暂存区的修改撤销,回到工作区;使文件返回到最近一次Git commit;
- **git rm file**;删除文件;
- **rm file**;文件管理器删除文件;不建议使用;
- **ssh-keygen -t rsa -C "youremail@example.com"**获得本地ssh加密;
- **git remote add origin git@github.com:michaelliao/learngit.git**;origin 是版本库的名称,后面跟github地址;
- **git push -u origin master**;第一次把本地的文件同步到网络上去;
- **git push origin master**以后提交时;
- **git clone git@github.com:michaelliao/gitskills.git**;将远程库的数据同步到本地;
- **git checkout -b dev**;创建一个dev的分支;
- **git branch** ;查看当前的分支;
- **git branch 分支名**;创建分支;
- **git checkout 分支名**;切换分支;
- **git merge 分支名**;合并指定分支到当前分支;
- **git branch -d 分支名**;删除分支;
- **git log --graph --pretty=oneline --abbrev-commit**;查看分支冲突解决后的分支合并情况;
- **git merge --no-ff -m "merge with no-ff" dev** 禁用fast forward
- **git stash**;将当前分支的工作区储藏起来,等恢复现场后,继续工作
- **git stash list**;查看当前分区的储藏list;
- **git stash drop** 删除储藏的;
- **git stash apply**;恢复储藏的;
- **git stash apply stash@{0}**恢复多次的储藏;
- **git stash pop**;恢复工作区的同时把储藏区删除;

```
修复bug时,我们会通过创建的新的bug分支进行修复,然后合并,最后删除;
当手头上工作没有完成是,先把工作现场 git stash一下,然后去修复bug,修复后再Git stash pop,回到工作现场
```
- **git branch -D <name>**强制删除分支;
- **git branch --set-upstream 分支名  origin/dev** 设置分支连接
- **git pull** 将远程库的版本同步下来;

```
如果Git pull提示"no tracking information" 则说明本地分支和远程分支的链接关系没有创建,用命令git branch --set-upstream branch-name origin/branch-name
```

- **git tag v1.0** ;打一个tag,标记的是最新commit的;
- **git tag v0.9 commit id**;
- **git show tagname**
- **git tag** 展示tag列表,是按照字母顺序列出的;
- **git tag -a tagname -m "说明文字"** 3628164
- **git tag -s v0.2 -m "signed version 0.2 released" fec145a,-s**用私钥PGP签名一个标签;
- **git tag -d v0.1**  删除标签;
- **git push origin v1.0** ;推送某个标签到远程;
- **git push origin --tags**;推送所有标签到远程;
### 删除远程标签
- **git tag -d v0.9** 本地删除;
- **git push origin :refs/tags/v0.9** 删除远程标签;
- **git config --global color.ui true**;git输出的文件显示颜色
- **git add -f App.class**强制添加到git;
- **git config --global alias.st status**  把 st 代表 status
- **git config --global alias.co checkout** 把 co 代表 checkout 
- **git config --global alias.ci commit**    把 ci 代表 commit
- **git config --global alias.br branch**   把 br 代表 branch;
- **git config --global alias.unstage 'reset HEAD'**
撤销修改;
- **git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"** 漂亮的输出日志;

- **cat .git/config**  查看快捷输入的配置;