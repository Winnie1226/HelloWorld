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
	
