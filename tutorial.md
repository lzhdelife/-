# git教程

https://blog.csdn.net/m0_48651355/article/details/120646834?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-120646834-blog-88870257.pc_relevant_multi_platform_whitelistv4&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-120646834-blog-88870257.pc_relevant_multi_platform_whitelistv4&utm_relevant_index=1



## 创建本地仓库并上传到github

```bash
git init //把这个目录变成Git可以管理的仓库
git add README.md //文件添加到仓库
git add . //不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
git commit -m "first commit" //把文件提交到仓库
git remote add origin git@github.com:lzhdelife/Weekly_Report.git //关联远程仓库
git push -u origin master //把本地库的所有内容推送到远程库上
```



更改后上传GitHub

```bash
git status -s  // 查状态
git add . //不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
git commit -m "first commit" //把文件提交到仓库
// git remote add origin git@github.com:lzhdelife/Weekly_Report.git 
//代码从远程clone下来，相当于已经关联远程仓库，不需要再次关联
git push -u origin master //把本地库的所有内容推送到远程库上
```



做出一些更改（测试）



## 详解git push -u origin main

`git push -u origin main` 是将本地分支 `main` 推送到远程仓库的命令，并且使用 `-u` 或 `--set-upstream` 参数来设置本地分支与远程分支的跟踪关系。

具体解释如下：

- `git push`: 这是 Git 命令，用于将本地分支的提交推送到远程仓库。
- `-u` 或 `--set-upstream`: 这是一个选项参数，用于设置本地分支与远程分支的跟踪关系。通过使用 `-u` 参数，Git 会将本地分支与指定的远程分支关联起来，以便在以后的推送中，您只需使用 `git push` 命令即可。
- `origin`: 这是远程仓库的名称。在这种情况下，`origin` 是一个常用的远程仓库名称，它通常用于指代您的远程仓库地址。
- `main`: 这是本地分支的名称。在这个例子中，假设您的本地分支名为 `main`，您将该分支的提交推送到远程仓库。

执行 `git push -u origin main` 命令后，Git 将会将您的本地分支 `main` 的提交推送到名为 `origin` 的远程仓库，并将 `main` 分支与远程仓库的同名分支建立关联。这样，以后您只需使用 `git push` 命令即可将更改推送到远程仓库。

请注意，根据您的项目设置和远程仓库的默认分支名称，您可能需要将 `main` 替换为您实际使用的本地分支名称，例如 `master`。确保在运行命令之前，将命令中的分支名称替换为您要推送的实际分支名称。



## git add  和 git commit 很繁琐，有简化办法吗

是的，Git 提供了一些简化办法来减少 `git add` 和 `git commit` 的繁琐。以下是两种常用的简化方法：

1. 使用 `git commit -a`：如果您已经对文件进行了修改并希望将所有修改一次性提交，可以使用 `-a` 选项来跳过 `git add` 步骤。这会将所有已修改的文件自动添加到暂存区并进行提交。请注意，这仅适用于已经被 Git 跟踪的文件。

   ```shell
   git commit -a -m "提交消息"
   ```

2. 使用 `git commit -am`：如果您只修改了已被 Git 跟踪的文件，并且不需要在提交之前将新文件添加到暂存区，可以使用 `-am` 选项将修改和提交合并到一个步骤中。

   ```shell
   git commit -am "提交消息"
   ```

这些简化方法可以减少手动执行 `git add` 的步骤，但请注意，它们并不适用于新增的未被 Git 跟踪的文件。对于新文件，仍然需要先使用 `git add` 将其添加到暂存区，然后再使用 `git commit` 进行提交。

尽管这些简化方法可以提高效率，但请确保在提交前仔细检查您的更改，以确保只提交您希望包含在每个提交中的内容。
