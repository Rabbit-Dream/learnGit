Git is a version control system.
Git is free software.

通过 git init 命令吧这个目录变成Git可以管理的仓库
用命令 git add “filename” 告诉 Git，把文件添加到仓库
用命令 git commit -m "更新说明" 告诉 Git,把文件提交到仓库
可以多次添加 一并提交

要随时掌握工作区的状态，使用 git status 命令查看
如果 git status 告诉我们文件被修改过，我们可以用 git diff 进一步查看修改内容

HEAD 指向的版本就是当前版本，因此，Git允许我们载版本的历史之间穿梭，使用命令 git reset --hard commit_id
穿梭前，用 git log 可以查看提交历史，以便确定要回到哪个版本
要重返未来，用 git reflog 查看命令历史，确定要回到未来的那个版本

暂存区是Git非常重要的概念，弄明白了暂存区，就明白了 Git 的很多操作到底干了什么

Git跟踪修改 每次修改，如果不用 git add 到暂存区，那就不会加入到 commit 中

场景1：当你改乱了工作区的某个文件的内容，想直接丢弃工作区的修改时，用命令 git checkout -- filename
场景2：当你不但改乱了工作区的某个文件的内容，还添加到了暂存区是，想丢弃修改，分两步：第一步用命令 git reset HEAD filename , 就回到了上面的场景1，第二步就是场景1的操作
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，那就版本退回吧，不过前提是没有推送到远程库

如果你删除了文件：
	1.确实要冲版本库中$删除该文件，那就用命令 git rm/add filename 删掉,并且 git commit -m "说明"
	2.误删，因为版本库里还有呢，所以可以很轻松地把误删的文件回复到最新版本(git checkout -- filename) 其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以一键还原
	注意: 你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容

远程管理：
	one: 创建 SSH Key  $ ssh-keygen -t rsa -C "youremail"  一路回车，使用默认值即可。由于这个Key也不用于军事目的，所以也无需设置密码。如果顺利边可以在用户主目录下的.ssh目录找到 id_rsa和id_rsa.pub两个文件，这两个就是 SSH Key 的秘钥，id_rsa是私钥，不可以泄露，id_rsa.pub是公钥，可以告诉别人。
	two:登录GitHub，打开“Account settings”,"SSH Key"页面，然后“Add SSH Key”,填上Title,在Key文本框里粘贴 id_rsa.pub 文件内容，最后点“Add Key”
	three:登录GitHub，然后，在右上角找到“new repository”,创建一个新的仓库，填入Repository name,点击“Create repository”按钮，就成功地床架了一个新的 Git 仓库
	four:要关联一个远程库，使用命令 git remote add origin git@server-name:path/repo-name.git ; 关联后，使用命令 git push -u origin master 第一次推送 master 分支的所有内容；此后，每次本地提交后，只要有必要，就可以使用命令 git push origin master 推送最新修改	
