### <font style="color:rgb(51, 51, 51);">git 常用命令</font>
![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737091078970-576d9df1-46b2-40db-a9ef-2719f6df9f7f.jpeg)

```plain
git init                                                  # 初始化本地git仓库（创建新仓库）
git config --global user.name "xxx"                       # 配置用户名
git config --global user.email "xxx@xxx.com"              # 配置邮件
git config --global color.ui true                         # git status等命令自动着色
git config --global color.status auto
git config --global color.diff auto
git config --global color.branch auto
git config --global color.interactive auto
git config --global --unset http.proxy                    # remove  proxy configuration on git
git clone git+ssh://git@192.168.53.168/VT.git             # clone远程仓库
git status                                                # 查看当前版本状态（是否修改）
git add xyz                                               # 添加xyz文件至index
git add .                                                 # 增加当前子目录下所有更改过的文件至index
git commit -m 'xxx'                                       # 提交
git commit --amend -m 'xxx'                               # 合并上一次提交（用于反复修改）
git commit -am 'xxx'                                      # 将add和commit合为一步
git rm xxx                                                # 删除index中的文件
git rm -r *                                               # 递归删除
git log                                                   # 显示提交日志
git log -1                                                # 显示1行日志 -n为n行
git log -5
git log --stat                                            # 显示提交日志及相关变动文件
git log -p -m
git show dfb02e6e4f2f7b573337763e5c0013802e392818         # 显示某个提交的详细内容
git show dfb02                                            # 可只用commitid的前几位
git show HEAD                                             # 显示HEAD提交日志
git show HEAD^                                            # 显示HEAD的父（上一个版本）的提交日志 ^^为上两个版本 ^5为上5个版本
git tag                                                   # 显示已存在的tag
git tag -a v2.0 -m 'xxx'                                  # 增加v2.0的tag
git show v2.0                                             # 显示v2.0的日志及详细内容
git log v2.0                                              # 显示v2.0的日志
git diff                                                  # 显示所有未添加至index的变更
git diff --cached                                         # 显示所有已添加index但还未commit的变更
git diff HEAD^                                            # 比较与上一个版本的差异
git diff HEAD -- ./lib                                    # 比较与HEAD版本lib目录的差异
git diff origin/master..master                            # 比较远程分支master上有本地分支master上没有的
git diff origin/master..master --stat                     # 只显示差异的文件，不显示具体内容
git remote add origin git+ssh://git@192.168.53.168/VT.git # 增加远程定义（用于push/pull/fetch）
git branch                                                # 显示本地分支
git branch --contains 50089                               # 显示包含提交50089的分支
git branch -a                                             # 显示所有分支
git branch -r                                             # 显示所有原创分支
git branch --merged                                       # 显示所有已合并到当前分支的分支
git branch --no-merged                                    # 显示所有未合并到当前分支的分支
git branch -m master master_copy                          # 本地分支改名
git checkout -b master_copy                               # 从当前分支创建新分支master_copy并检出
git checkout -b master master_copy                        # 上面的完整版
git checkout features/performance                         # 检出已存在的features/performance分支
git checkout --track hotfixes/BJVEP933                    # 检出远程分支hotfixes/BJVEP933并创建本地跟踪分支
git checkout v2.0                                         # 检出版本v2.0
git checkout -b devel origin/develop                      # 从远程分支develop创建新本地分支devel并检出
git checkout -- README                                    # 检出head版本的README文件（可用于修改错误回退）
git merge origin/master                                   # 合并远程master分支至当前分支
git cherry-pick ff44785404a8e                             # 合并提交ff44785404a8e的修改
git push origin master                                    # 将当前分支push到远程master分支
git push origin :hotfixes/BJVEP933                        # 删除远程仓库的hotfixes/BJVEP933分支
git push --tags                                           # 把所有tag推送到远程仓库
git fetch                                                 # 获取所有远程分支（不更新本地分支，另需merge）
git fetch --prune                                         # 获取所有原创分支并清除服务器上已删掉的分支
git pull origin master                                    # 获取远程分支master并merge到当前分支
git mv README README2                                     # 重命名文件README为README2
git reset --hard HEAD                                     # 将当前版本重置为HEAD（通常用于merge失败回退）
git rebase
git branch -d hotfixes/BJVEP933                           # 删除分支hotfixes/BJVEP933（本分支修改已合并到其他分支）
git branch -D hotfixes/BJVEP933                           # 强制删除分支hotfixes/BJVEP933
git ls-files                                              # 列出git index包含的文件
git show-branch                                           # 图示当前分支历史
git show-branch --all                                     # 图示所有分支历史
git whatchanged                                           # 显示提交历史对应的文件修改
git revert dfb02e6e4f2f7b573337763e5c0013802e392818       # 撤销提交dfb02e6e4f2f7b573337763e5c0013802e392818
git ls-tree HEAD                                          # 内部命令：显示某个git对象
git rev-parse v2.0                                        # 内部命令：显示某个ref对于的SHA1 HASH
git reflog                                                # 显示所有提交，包括孤立节点
git show HEAD@{5}
git show master@{yesterday}                               # 显示master分支昨天的状态
git log --pretty=format:'%h %s' --graph                   # 图示提交日志
git show HEAD~3
git show -s --pretty=raw 2be7fcb476
git stash                                                 # 暂存当前修改，将所有至为HEAD状态
git stash list                                            # 查看所有暂存
git stash show -p stash@{0}                               # 参考第一次暂存
git stash apply stash@{0}                                 # 应用第一次暂存
git grep "delete from"                                    # 文件中搜索文本“delete from”
git grep -e '#define' --and -e SORT_DIRENT
git gc
git fsck
```

### <font style="color:rgb(79, 79, 79);">Git 创建仓库</font>
<font style="color:rgb(77, 77, 77);">创建一个git仓库有如下几种方式：</font>

+ **<font style="color:rgba(0, 0, 0, 0.75);">git init</font>**<font style="color:rgba(0, 0, 0, 0.75);">：初始化一个git仓库</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git clone</font>**<font style="color:rgba(0, 0, 0, 0.75);">：clone一个git仓库</font>

**<font style="color:rgb(77, 77, 77);">下面对这几种方式进行详细介绍：</font>**

#### <font style="color:rgba(0, 0, 0, 0.75);">git init</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">Git使用git init命令来初始化一个Git仓库，执行完git init命令后，会生成一个.git目录，该目录包含了资源数据，且只会在仓库的根目录生成。</font>

<font style="color:rgb(77, 77, 77);">如果用当前目录作为Git仓库，则只需要执行如下命令：</font>

```plain
git init
```

<font style="color:rgb(77, 77, 77);">执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014009-ef38ffb8-70ba-47c1-8538-9626e0c7a819.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">执行该命令之后，就可以在当前目录下生成.init文件夹，并且会默认生成一个master分支。</font>

<font style="color:rgb(77, 77, 77);">如果要在指定的目录下生成仓库，则指令如下：</font>

```plain
git init newDir
```

<font style="color:rgb(77, 77, 77);">newDir为仓库的路径，执行完成之后，会在newDir目录下生成一个.git目录。具体的执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014098-38f3e6e2-1f72-4a3e-af1d-b8b6956a9333.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">执行该命令之后，就可以在当前目录下生成newtest文件夹，并在改文件夹下生成.init文件夹。</font>

#### <font style="color:rgba(0, 0, 0, 0.75);">git clone</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">使用git clone命令可以从Git仓库拷贝项目，类似于SVN中的 svn checkout，命令格式为：</font>

```plain
git clone <url> [directory]
```

<font style="color:rgb(77, 77, 77);">url为git仓库地址，directory为本地目录，比如，要克隆某个Git 代码仓库，可以用下面的命令：</font>

```plain
git clone git://github.com/schacon/grit.git
```

<font style="color:rgb(77, 77, 77);">执行完成之后会在当前目录下生成仓库，如果要指定目录下生成，则可以在后面加一个具体的位置路径，如：</font>

```plain
git clone git://github.com/schacon/grit.git newgit
```

<font style="color:rgb(77, 77, 77);">如下为clone一个仓库的执行结果：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014084-17d83ae6-4992-4065-8175-1556eeffcc5a.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git clone 时，可以用不同的协议，包括 ssh, git, https 等，其中最常用的是 ssh，因为速度较快，还可以配置公钥免输入密码，各种写法格式如下：</font>

```plain
git clone git@github.com/schacon/grit.git         --SSH协议
git clone git://github.com/schacon/grit.git          --GIT协议
git clone https://github.com/schacon/grit.git      --HTTPS协议
```

### <font style="color:rgb(79, 79, 79);">Git 基本指令的使用</font>
<font style="color:rgb(77, 77, 77);">下面介绍一下git中常用的几种命令：</font>

+ **<font style="color:rgba(0, 0, 0, 0.75);">git config</font>**<font style="color:rgba(0, 0, 0, 0.75);">：配置信息</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git add</font>**<font style="color:rgba(0, 0, 0, 0.75);">：添加文件到缓存命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git status</font>**<font style="color:rgba(0, 0, 0, 0.75);">：查看文件的状态命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git diff</font>**<font style="color:rgba(0, 0, 0, 0.75);">：查看更新的详细信息命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git commit</font>**<font style="color:rgba(0, 0, 0, 0.75);">：提交命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git reset HEAD</font>**<font style="color:rgba(0, 0, 0, 0.75);">：取消缓存命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git rm</font>**<font style="color:rgba(0, 0, 0, 0.75);">：删除命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git mv</font>**<font style="color:rgba(0, 0, 0, 0.75);">：移动或重命名命令</font>

**<font style="color:rgb(77, 77, 77);">下面对这几个命令进行详细介绍：</font>**

#### <font style="color:rgba(0, 0, 0, 0.75);">git config</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">我们可以通过git config来配置用户名和邮箱地址，便于我们将代码提交到远程仓库，具体格式如下：</font>

```plain
git config --global user.name '你的用户名'
git config --global user.email '你的邮箱'
```

#### <font style="color:rgba(0, 0, 0, 0.75);">git add</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git add 命令可将文件添加到缓存，如新项目中，添加所有文件很普遍，可以使用如下命令：</font>

```plain
git add .
```

<font style="color:rgb(77, 77, 77);">当然我们也可以指定某一类文件，如将java文件添加到缓存中，可以使用如下命令：</font>

```plain
it add *.java
```

<font style="color:rgb(77, 77, 77);">如：我们可以创建两个文件，将它添加的缓存中，具体操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089014095-e7774745-941f-4b33-b996-0ad58ead05b7.png)

#### <font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git status</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">我们可以使用 git status 命令来查看相关文件的状态，直接执行如下命令：</font>

```plain
git status
```

<font style="color:rgb(77, 77, 77);">如果有修改的文件，则执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014456-4b89390b-1218-488a-81aa-f42daa7bf8d7.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">根据上面git status命令的提示内容，我们可以得到三种处理情况：</font>

+ <font style="color:rgba(0, 0, 0, 0.75);">暂存文件的命令：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git add <文件名></font>**
+ <font style="color:rgba(0, 0, 0, 0.75);">放弃未暂存文件的修改命令：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git checkout – <文件名></font>**
+ <font style="color:rgba(0, 0, 0, 0.75);">将被修改的文件暂存并提交的命令：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git commit -a</font>**

<font style="color:rgb(77, 77, 77);">如果你对Git的各种状态比较熟悉了，也可以使用 git status -s 来查看简写的状态，这种简写的状态和SVN上的差不多 M - 被修改，A - 被添加，D - 被删除，R - 重命名，?? - 未被跟踪 等等。如果有修改的文件，则执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014524-8e41d624-4c4a-4696-bb88-ff4191bd84a2.jpeg)

#### <font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git diff</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">执行 git diff 来查看更新的详细信息，与git status不同的是，git status只显示更新的状态，而 git diff 可以显示已写入缓存与已修改但尚未写入缓存的改动的区别具体的详细信息。</font>

+ <font style="color:rgba(0, 0, 0, 0.75);">尚未缓存的改动：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git diff</font>**
+ <font style="color:rgba(0, 0, 0, 0.75);">查看已缓存的改动：</font><font style="color:rgba(0, 0, 0, 0.75);"> </font>**<font style="color:rgba(0, 0, 0, 0.75);">git diff --cached</font>**
+ <font style="color:rgba(0, 0, 0, 0.75);">查看已缓存的与未缓存的所有改动：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git diff HEAD</font>**
+ <font style="color:rgba(0, 0, 0, 0.75);">显示摘要而非整个 diff：</font>**<font style="color:rgba(0, 0, 0, 0.75);">git diff --stat</font>**

<font style="color:rgb(77, 77, 77);">如：我们在修改一下test.txt文件内容，使用git diff查看修改详细信息：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089014590-f57b13d2-8337-4424-b3ec-0e57f1c44a5e.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">之后我们将修改的内容add到缓存中，再使用git diff查看修改详细信息：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089014649-489ea67e-b764-4297-bdc6-c1fb25244ebb.png)



#### <font style="color:rgba(0, 0, 0, 0.75);">git commit</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git commit 将缓存区内容添加到仓库中，可以在后面加-m选项，以在命令行中提供提交注释，格式如下：</font>

```plain
git commit -m "第一次版本提交"
```

<font style="color:rgb(77, 77, 77);">如果你觉得 每次 commit之前要add一下，想跳过add这一步，可以直接使用 -a选项,如：</font>

```plain
git commit -am "第一次版本提交"
```

<font style="color:rgb(77, 77, 77);">如：我们可以创建一个文件，并将它添加打缓存，之后在提交，具体操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089014628-3c25b6cd-b776-4065-8a11-742e8b8a39f1.jpeg)

#### <font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git reset HEAD</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git reset HEAD 命令用于取消已缓存的内容，如我们要取消已提交的test.txt文件，可以如下使用：</font>

```plain
git reset HEAD test.txt
```

<font style="color:rgb(77, 77, 77);">执行完之后，再使用commit提交时，test.txt文件不会被提交。  
</font><font style="color:rgb(77, 77, 77);">如：我们先修改test1.txt，test2.txt文件，之后再都添加到缓存，然后再使用git reset HEAD命令恢复test1.txt，最后再使用提交，具体操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089014975-7ccb85b0-6c5a-4ed8-b101-1e5b590562ea.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以看出，修改的test1文件经过git reset HEAD后，没有被提交上去。简而言之，执行 git reset HEAD 以取消之前 git add 添加。  
</font>**<font style="color:rgb(77, 77, 77);">git rm</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">如果只是简单地从工作目录中手工删除文件，运行 git status 时就会在 Changes not staged for commit 的提示。要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除，然后提交。可以如下使用：</font>

```plain
git rm <file>
```

<font style="color:rgb(77, 77, 77);">如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f</font>

```plain
git rm -f <file>
```

<font style="color:rgb(77, 77, 77);">如果把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用 --cached 选项即可</font>

```plain
git rm --cached <file>
```

<font style="color:rgb(77, 77, 77);">可以</font><font style="color:rgb(252, 85, 49);">递归</font><font style="color:rgb(77, 77, 77);">删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件：</font>

```plain
git rm –r *
```

<font style="color:rgb(77, 77, 77);">如：我们移除上面所创建的hello.java文件：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015018-90868452-bd87-4392-9ce7-df21545976ce.jpeg)



#### <font style="color:rgba(0, 0, 0, 0.75);">git mv</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git mv 命令用于移动或重命名一个文件、目录、软连接，如要将一个test.txt文件重命名为newtest.txt，则可以使用如下命令：</font>

```plain
git mv test.txt newtest.txt
```

<font style="color:rgb(77, 77, 77);">如：我们将上面的test1.txt文件重命名为test.txt:  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015045-ad7ce4e7-3a36-403e-aaa9-01fe84b5fcda.jpeg)

### <font style="color:rgb(79, 79, 79);">Git的分支管理</font>
<font style="color:rgb(77, 77, 77);">几乎每种</font><font style="color:rgb(252, 85, 49);">版本控制系统</font><font style="color:rgb(77, 77, 77);">都支持分支管理，使用分支我们可以从主干中分离出来，然后继续开发，不影响主干。下面介绍一下Git中分支常用的命令：</font>

+ **<font style="color:rgba(0, 0, 0, 0.75);">git branch</font>**<font style="color:rgba(0, 0, 0, 0.75);">：查看分支命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git branch (branchname)</font>**<font style="color:rgba(0, 0, 0, 0.75);">：创建分支命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git checkout (branchname)</font>**<font style="color:rgba(0, 0, 0, 0.75);">：切换分支命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git merge</font>**<font style="color:rgba(0, 0, 0, 0.75);">：合并分支命令</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git branch -d (branchname)</font>**<font style="color:rgba(0, 0, 0, 0.75);">：删除分支命令</font>

**<font style="color:rgb(77, 77, 77);">下面分别对这些命令进行详细介绍：</font>**

**<font style="color:rgba(0, 0, 0, 0.75);">git branch</font>**<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git branch可以查看分支，也可以创建分支，如果没有参数时，git branch会列出你在本地的分支；如果有参数时，git branch就会创建改参数的分支。</font>

<font style="color:rgb(77, 77, 77);">如果要查看分支，命令格式如下：</font>

```plain
git branch
```

<font style="color:rgb(77, 77, 77);">在bash执行的效果如下图所示：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015131-69c66414-df86-4353-875a-9fe23d415399.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">当我们想创建分支时，可以在后面加参数，命令格式如下：</font>

```plain
git branch  branchname
```

<font style="color:rgb(77, 77, 77);">如我们想创建一个test的分支，可以如下操作：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015186-92bdd774-b09d-4f1e-bdaf-63902f37e0a8.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">现在我们可以看到，多了一个新的分支test。而master分支在我们执行git init的时候，缺省情况下 Git 就会为你创建 master 分支。</font>

<font style="color:rgb(77, 77, 77);"></font>

#### <font style="color:rgba(0, 0, 0, 0.75);">git checkout (branchname)</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git checkout可以切换分支，命令格式如下：</font>

```plain
git checkout branchname
```

<font style="color:rgb(77, 77, 77);">如果我们想切换到上面刚刚创建的test分支中，可以如下操作：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015594-7af1755a-67f3-4f06-9e46-5ea190eab619.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以看到，没有执行之前，当前的分支是master，当执行之后，当前的分支是test，这个时候可以可以在切换后的分支中继续操作，而不会影响到其他分支。  
</font><font style="color:rgb(77, 77, 77);">我们也可以使用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">git checkout -b (branchname)</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">命令来创建新分支并立即切换到该分支下，从而在该分支中操作。如，我们想创建一个newtest分支，并创建后就切换到该分支下，可以如下操作：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015580-0fb97212-fa3e-4fbc-b094-10948360770a.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以看出，执行之前还在master分支中，执行之后，直接进入newtest分支了。</font>

<font style="color:rgb(77, 77, 77);"></font>

#### <font style="color:rgba(0, 0, 0, 0.75);">git merge</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git merge命令可以将任意分支合并到到当前分支中去，命令格式如下：</font>

```plain
git merge branchname
```

<font style="color:rgb(77, 77, 77);">如：我们新建一个newtest分支，并在其中增加test3.txt文件，之后在master中将newtest分支的修改合并到master，结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089015677-fb502363-b19b-401a-b96f-be37d8816950.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可见master中也存在test3.txt文件了。  
</font>**<font style="color:rgb(77, 77, 77);">合并冲突</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">合并的时候，最大的难点就是冲突了，合并并不仅仅是简单的文件添加、移除的操作，Git 也会合并修改，如果我们在两个分支中同时修改了同一个文件，这时再合并，就可能会产生冲突，冲突并不可怕，可怕的是要怎样去解决，下面以一个小的例子来展示一下合并是冲突的解决。  
</font><font style="color:rgb(77, 77, 77);">还是用上面的那个仓库，现在有两个分支：master、newtest，两个分支中都要test.txt文件，这个时候我们都这个两个仓库的文件都进行修改，之后再提交，最后将newtest合并到master中，具体的操作如下：  
</font><font style="color:rgb(77, 77, 77);">1、先修改分支：master、newtest中的test.txt文件，并提交：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089015724-5d7f4080-cd52-441a-a3dd-8d32c9cb27ca.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">2、之后再将newtest分支修改的内容合并到master分支中：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089015723-7e484fb4-cf28-4f38-86c3-f5fca1f722e1.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以看到newtest分支修改的内容和master分支修改的内容发生了冲突，这是根据具体的情况去解决，如下，我们保留两个分支都有的，之后再add，在commit就可以了：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089016109-8912b926-36fb-44fc-bae2-c189f8fb0b72.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">到此一个简单的合并就完成了。实际项目开发中，合并比这要复杂的多，要结合具体的情况去操作。</font>

<font style="color:rgb(77, 77, 77);"></font>

#### <font style="color:rgba(0, 0, 0, 0.75);">git branch -d (branchname)</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git branch -d可以删除分支，删除分支命令格式如下：</font>

```plain
git branch -d (branchname)
```

<font style="color:rgb(77, 77, 77);">如：我们要删除test分支：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089016099-12212bf0-62e8-4bd5-9b69-0a701859911f.png)

### <font style="color:rgb(79, 79, 79);">Git查看提交历史</font>
<font style="color:rgb(77, 77, 77);">在使用 Git 提交了若干更新之后，又或者克隆了某个项目，想回顾下提交历史，我们可以使用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">git log</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">命令查看，如，我们想列出历史提交记录如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089016336-24f207d5-1f8d-4a2d-8f4a-97afa1b44116.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">下面介绍查看历史记录的几种选项：</font>

+ **<font style="color:rgba(0, 0, 0, 0.75);">–oneline</font>**<font style="color:rgba(0, 0, 0, 0.75);"> </font><font style="color:rgba(0, 0, 0, 0.75);">：查看历史记录的简洁版本</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">–graph</font>**<font style="color:rgba(0, 0, 0, 0.75);"> </font><font style="color:rgba(0, 0, 0, 0.75);">：查看历史中什么时候出现了分支、合并</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">–reverse</font>**<font style="color:rgba(0, 0, 0, 0.75);"> </font><font style="color:rgba(0, 0, 0, 0.75);">：逆向显示所有日志</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">–author</font>**<font style="color:rgba(0, 0, 0, 0.75);"> </font><font style="color:rgba(0, 0, 0, 0.75);">：查找指定用户的提交日志</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">–since、–before、 --until、–after</font>**<font style="color:rgba(0, 0, 0, 0.75);">： 指定筛选日期</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">–no-merges</font>**<font style="color:rgba(0, 0, 0, 0.75);"> </font><font style="color:rgba(0, 0, 0, 0.75);">：选项以隐藏合并提交</font>

<font style="color:rgb(77, 77, 77);">我们可以用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">–oneline</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">选项来查看历史记录的简洁版本：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089016296-f717ee2f-7d43-4303-8176-9594b707527d.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">我们还可以用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">–graph</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">选项，查看历史中什么时候出现了分支、合并：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089016373-a22aa0d1-5afe-4995-9e63-91d4911fc752.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">这样我们可以更清楚明了地看到何时工作分叉、又何时归并，也可以用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">–reverse</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">参数来逆向显示所有日志：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089016693-7503c775-9f9c-4c08-b235-e4dcb6e623f2.png)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">如果只想查找指定用户的提交日志可以使用命令：</font>**<font style="color:rgb(77, 77, 77);">git log --author</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">, 例如，比方说我们要找 Git 源码中qtqt提交的部分：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089016646-0f9ec751-95d0-40f9-8684-7cf60f9d2622.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">如果你要指定日期，可以执行几个选项：–since 和 --before，但是你也可以用 --until 和 --after，–no-merges 选项以隐藏合并提交。</font>

<font style="color:rgb(77, 77, 77);">例如，如果我要看 Git 项目中八月一日前且在七月二十九日之后的所有提交，我可以执行这个：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089016920-87c462f3-3ea0-4970-908f-21274d71386b.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">多数情况下，了解每条提交与那个分支／标签关联是很有用的。</font>**<font style="color:rgb(77, 77, 77);">–decorate</font>**<font style="color:rgb(77, 77, 77);"> </font><font style="color:rgb(77, 77, 77);">标记让git log展示所有指向每个提交引用（如分支，标签等）,如:  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017094-ed67521f-cf4b-4901-b00b-ba58c86ebddc.jpeg)

### <font style="color:rgb(79, 79, 79);">Git 标签</font>
<font style="color:rgb(77, 77, 77);">使用标签可以很方便的永远的记住那个特别的提交快照，比如：我们发一个新的版本时，可以给它加一个“vx.x”版本，这样你可以使用git tag给它打上标签。  
</font>**<font style="color:rgb(77, 77, 77);">创建新标签</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以使用</font><font style="color:rgb(77, 77, 77);"> </font>**<font style="color:rgb(77, 77, 77);">git tag -a vx.x</font>**<font style="color:rgb(77, 77, 77);">来创建一个标签。a 选项意为"创建一个带注解的标签"。 不用 -a 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解。  
</font><font style="color:rgb(77, 77, 77);">如：我们为我们上的例子创建一个标签：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017105-31745dfb-64a9-4ab6-9a4e-ca09803abbdf.jpeg)<font style="color:rgb(77, 77, 77);">  
</font>**<font style="color:rgb(77, 77, 77);">追加标签</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">如果我们忘了给某个提交打标签，又将它发布了，我们可以给它追加标签。如，假设我们发布了提交 d6f7147，但是那时候忘了给它打标签。 我们现在也可以：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017131-3ed2ec91-23bf-445d-a05f-acad04f6101a.jpeg)<font style="color:rgb(77, 77, 77);">  
</font>**<font style="color:rgb(77, 77, 77);">查看标签</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">如果我们要查看所有标签可以使用以下命令：</font>

```plain
git tag
```

<font style="color:rgb(77, 77, 77);">执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017157-7b60f983-a20e-4f63-8b79-a2e5cbb0ec37.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">指定标签信息命令：</font>

```plain
git tag -a <tagname> -m "某某标签"
```

<font style="color:rgb(77, 77, 77);">PGP签名标签命令：</font>

```plain
git tag -s <tagname> -m "某某标签"
```

### <font style="color:rgb(79, 79, 79);">Git 远程仓库</font>
<font style="color:rgb(77, 77, 77);">前面我们使用到的 Git 命令都是在本地执行，如果你想通过 Git 分享你的代码或者与其他开发人员合作。 你就需要将数据放到一台其他开发人员能够连接的服务器上。本本将使用 Github 作为远程仓库，来介绍Git 远程仓库的使用。  
</font><font style="color:rgb(77, 77, 77);">下面介绍远程仓库常用的几种指令：</font>

+ **<font style="color:rgba(0, 0, 0, 0.75);">git remote add</font>**<font style="color:rgba(0, 0, 0, 0.75);">：添加远程仓库</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git remote</font>**<font style="color:rgba(0, 0, 0, 0.75);">：查看当前的远程仓库</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git fetch</font>**<font style="color:rgba(0, 0, 0, 0.75);">、</font>**<font style="color:rgba(0, 0, 0, 0.75);">git pull</font>**<font style="color:rgba(0, 0, 0, 0.75);">：提取远程仓仓库</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git push</font>**<font style="color:rgba(0, 0, 0, 0.75);">：推送到远程仓库</font>
+ **<font style="color:rgba(0, 0, 0, 0.75);">git remote rm</font>**<font style="color:rgba(0, 0, 0, 0.75);">：删除远程仓库</font>

#### <font style="color:rgb(77, 77, 77);">git remote add</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git remote add可以添加一个远程仓库，其命令格式如下：</font>

```plain
git remote add [alias] [url]
```

<font style="color:rgb(77, 77, 77);">参数[alias]为别名， [url]为远程仓库的地址，如：我们可以将https://github.com/qtqt/test.git</font>

<font style="color:rgb(77, 77, 77);">仓库添加到本地，并命名为test，操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017462-50d4ad3f-28c4-47f2-a0b7-ab4873bab714.jpeg)

#### <font style="color:rgb(77, 77, 77);">git remote</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git remote可以查看当前有哪些远程仓库，执行结果如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017564-47d5ed5b-8b5c-4451-b840-0b5f8aa182bc.jpeg)<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">可以看出，有上面添加的别名为test仓库。</font>

#### <font style="color:rgba(0, 0, 0, 0.75);">git fetch、git pull</font>
<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">git fetch可以提取远程仓库的数据，如果有多个远程仓库，我们可以在后面加仓库的别名，操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/jpeg/42646381/1737089017569-c05f1929-ea04-4030-9358-d8c51874310b.jpeg)<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">该命令执行完后需要执行git merge 远程分支到你所在的分支。假设你配置好了一个远程仓库，并且你想要提取更新的数据，你可以首先执行 git fetch [alias] 告诉 Git 去获取它有你没有的数据，然后你可以执行 git merge [alias]/[branch] 以将服务器上的任何更新（假设有人这时候推送到服务器了）合并到你的当前分支。操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089017576-926241b6-59b4-4e28-8eae-eaa127cf92c8.png)<font style="color:rgba(0, 0, 0, 0.75);">  
</font><font style="color:rgba(0, 0, 0, 0.75);">执行完成之后可以在本地仓库找到远程仓库的文件。使用这种方式只能保证本地是一个空的仓库，如果非空，则会报：fatal: refusing to merge unrelated histories错误。</font>

**<font style="color:rgb(77, 77, 77);">git pull</font>**<font style="color:rgb(77, 77, 77);">命令用于从另一个存储库或本地分支获取并集成(整合)，在默认模式下，git pull是git fetch后跟git merge FETCH_HEAD的缩写，使用格式：</font>

```plain
git pull [options] [<repository> [<refspec>…]]
```

<font style="color:rgb(77, 77, 77);">如：我们可以将远程仓库pull到本地，如果本地仓库和远程仓库实际上是独立的两个仓库，–allow-unrelated-history选项来解决。  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089017659-8ecf5d06-8bfe-411e-a816-9bb35f75f2a2.png)<font style="color:rgb(77, 77, 77);">  
</font>**<font style="color:rgb(77, 77, 77);">git fetch</font>**<font style="color:rgb(77, 77, 77);">和</font>**<font style="color:rgb(77, 77, 77);">git pull</font>**<font style="color:rgb(77, 77, 77);">的区别：</font>

1. <font style="color:rgb(77, 77, 77);">git fetch：相当于是从远程获取最新版本到本地，不会自动合并。</font>
2. <font style="color:rgb(77, 77, 77);">git pull：相当于是从远程获取最新版本并merge到本地。</font>
3. **<font style="color:rgb(77, 77, 77);">git push</font>**<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git push 推送你的新分支与数据到某个远端仓库命令，格式如下：</font>

```plain
git push [alias] [branch]
```

<font style="color:rgb(77, 77, 77);">如：我们可以将前面提交的文件push到远程仓库中：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089018152-59538720-ebbd-4c24-85f8-55c9876279f9.png)

#### <font style="color:rgb(77, 77, 77);">git remote rm</font>
<font style="color:rgb(77, 77, 77);">  
</font><font style="color:rgb(77, 77, 77);">git remote rm删除远程仓库，格式如下：</font>

```plain
git remote rm [别名]
```

<font style="color:rgb(77, 77, 77);">如：我们可以先添加一个test2仓库，之后再删除它，操作如下：  
</font>![](https://cdn.nlark.com/yuque/0/2025/png/42646381/1737089018149-62d8d57f-afd7-4de4-a3ef-02067e9d5194.png)

<font style="color:rgb(77, 77, 77);">好了，到此基本上将Git常用的操作介绍完了。</font>

<font style="color:rgba(0, 0, 0, 0.75);"></font>

