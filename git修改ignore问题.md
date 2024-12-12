问题：比如我的android 目录下面有一个local.properties文件，我在gitignore已经添加了/local.properties，但是还是会把文件提交到仓库，

出现这种情况，通常是因为local.properties文件已经被Git跟踪了。.gitignore文件只能忽略那些原来没有被跟踪的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的
。要解决这个问题，你需要执行以下步骤：

从Git仓库中移除已跟踪的文件：
使用git rm --cached命令将local.properties文件从Git的暂存区（也就是跟踪列表）中移除，但保留在工作目录中。命令如下：

git rm --cached local.properties
重新添加所有文件：
使用git add .命令重新添加所有文件，此时.gitignore文件中的规则将生效，指定的文件将被忽略：

git add .
提交更改：
最后，提交这些更改：

git commit -m "Remove local.properties from tracking and update .gitignore"
推送更改到远程仓库：
使用git push命令将更改推送到远程仓库：

git push
执行完这些步骤后，local.properties文件应该不会再被提交到Git仓库中了。如果还有其他文件也需要从Git仓库中移除，可以重复上述步骤。