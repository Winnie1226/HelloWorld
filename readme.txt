1、创建目录并指定仓库
   git init

2、创建文件并将文件放置在仓库目录下

    readme.txt
	
3、添加文件到仓库
	1、git add readme.txt
	2、git commit 告诉git ，把文件体体积到仓库
	如：git commit  -m “第一次提交”
4、仓库文件对比
	1、对比本地仓库和上传仓库文件：git status
	2、查看对比后的不同的结果：git diff
	备注：绿色的为不同的

5、版本回退
	1、查看上次日志记录：git log / git log --pretty=oneline ------提交历史
	2、根据commit id 进行文件回滚：git reset --hard id(id可以只添加部分，git会自动匹配)
	3、查看回滚后的文件：cat XXXX(也可以在本地参考直接查看文件)
	5、若电脑重启后，想回滚文件到最新版本时，查找commit id的方法：git reflog  -----命令历史
	
6、撤销修改
	
	1、修改了工作区文件，但没有提交到暂缓区的撤销方式：
	git checkout -- readme.txt
	
	意义：
	一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

	一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

	总之，就是让这个文件回到最近一次git commit或git add时的状态。
	
	2、修改了暂缓区进行撤销方式，即做了git add 操作：
	git reset  HEAD readme.txt
	用命令git reset HEAD <file>可以把暂存区的修改撤销掉（unstage），重新放回工作区
	
	3、从暂存区提交到了版本库后的撤销：
	用版本回退的方式即可。
	
	总结：
		场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

		场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

		场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
		
7、删除文件
		1、rm file 删除工作区文件   ----可以用git checkout --file 恢复
		2、git rm file 删除工作区和缓存区的文件 ----分两步恢复文件：1、git reset HEAD file  2、git checkout --file 
		
		总结：git rm file 用于删除一个文件。若想恢复到之前修改的内容需要用到版本回退
		
		
二、远程仓库

	1、远程仓库创建
	
	2、远程仓库和本地仓库关联
		1、克隆远程仓库到本地
		2、关联本地仓库到远程
		  在本地仓库下运行：git remote add origin git@github.com:“github的账号”/learngit.git
	
	3、本地仓库内容推送到远程库
		git push -u origin maste
		备注：远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令
		
		总结：
		要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；

		关联后，使用命令git push -u origin master第一次推送master分支的所有内容；

		此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改
		
三、仓库地址查看：
	1、运行bash 输入命令"git remote -v" 