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


