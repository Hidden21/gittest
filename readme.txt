1 Git简介
--1.1 Git的诞生
--1.2 集中式vs分布式
2 安装Git
3 创建版本库
	初始化一个Git仓库，使用git init命令。
	添加文件到Git仓库，分两步：
	第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	第二步，使用命令git commit，完成。
4 时光机穿梭
	要随时掌握工作区的状态，使用git status命令。
	如果git status告诉你有文件被修改过，用git diff可以查看修改内容。git diff HEAD -- readme.txt
--4.1 版本回退
	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。（commit_id可以为HEAD^ 或 HEAD~100）
	穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。(显示少量信息加上 --pretty=oneline参数)
	要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
--4.2 工作区和暂存区
--4.3 管理修改
--4.4 撤销修改
	场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。（命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令）
	场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
	场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
--4.5 删除文件
	命令git rm用于删除一个文件
5 远程仓库
	本地Git仓库和GitHub仓库之间的传输是通过SSH加密的。
	第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
		在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
		ssh-keygen -t rsa -C "youremail@example.com"
	第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面
		将id_rsa.pub的内容贴到github上
--5.1 添加远程库
	要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
	关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
	此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改
	eg：同步 git remote add origin git@github.com:Hidden21/WebApp.git
			https://github.com/Hidden21/WebApp.git
--5.1 从远程库克隆
6 分支管理
--6.1 创建与合并分支
	Git鼓励大量使用分支：
		查看分支：git branch
		创建分支：git branch <name>
		切换分支：git checkout <name>
		创建+切换分支：git checkout -b <name>
		合并某分支到当前分支：git merge <name>
		删除分支：git branch -d <name>
--6.2 解决冲突
	当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
	用git log --graph命令可以看到分支合并图
--6.3 分支管理策略
--6.4 Bug分支
--6.5 Feature分支
--6.6 多人协作
7 标签管理
--7.1 创建标签
--7.2 操作标签
8 使用GitHub
9 自定义Git
--9.1 忽略特殊文件
--9.2 配置别名
--9.3 搭建Git服务器
10 期末总结

哈哈