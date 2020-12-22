#时间：2020年12月22日16:33:40
#作者：李珊
#内容：Git的基本使用教程
#操作系统：Windows10

安装Git，官网下载地址：

> [https://git-scm.com/download/win](https://git-scm.com/download/win)

使用目标1：在本地对项目进行版本控制，并上传到服务器端
使用目标2：下载服务器端的项目到本地，修改后再上传到服务器

 1. 基础配置
	1.1 配置用户名、邮箱（用于身份验证）

	    $ git config --global user.name [name]
	    $ git config --global user.email [email]

 2. 获取git仓库
	方法一：直接在本地磁盘上创建一个仓库
	进入目标文件夹，初始化本地git仓库，生成一个.git隐藏文件夹

	    $ git init
    
	方法二：从服务器克隆一个已存在的仓库（需联网）
	在GitHub或Gitee上寻找一个仓库链接地址，复制url链接
	    
	    $ git clone [url]
    
	例如：git clone https://github.com/lishan666/git_tutor.git
	
	自定义克隆的项目名，在末尾添加新的项目名称即可
	例如：git clone https://github.com/lishan666/git_tutor.git myproject
	
	备注：git支持https协议，也支持ssh协议
	例如：git clone git@github.com:lishan666/git_tutor.git
	
 3. 文件操作
	 3.1 检查文件状态
		
	查看完整信息
		
		$ git status
	
	查看简洁信息，添加参数-s

		$ git status -s
	 
	 3.2 跟踪新文件，即添加文件到暂存区，或暂存已修改文件

		 $ git add [files1] [files2] [...]
	
	备注：可跟踪一个文件，也可以跟踪多个文件或整个文件夹
	例如：
	
		git add readme.txt
		git add readme.txt hello.c welcome.h
		git add data
		
	特别的，添加当前文件目录下的所有文件
			
		$ git add ./
		
	3.3 忽略文件
	创建一个名为 .gitignore的文件，列出要忽略的文件的模式
	
		$ touch .gitignore
		$ cat .gitignore
		*.[oa]
		*~
		tmp/
 	第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。
 	第二行告诉 Git 忽略所有名字以波浪符（~）结尾的文件
 	第三行告诉 Git 忽略tmp文件夹下的所有文件
	此外，你可能还需要忽略 log、 pid 等目录。 
	
	文件 .gitignore 的格式规范如下：

	• 所有空行或者以 # 开头的行都会被 Git 忽略。
	• 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。
	• 匹配模式可以以（/）开头防止递归。
	• 匹配模式可以以（/）结尾指定目录。
	• 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反
	
	3.4 查看暂存前后文件变化
	
		$ git diff
	
	3.5 提交更新
				
		$ git commit
	
	提交时，添加备注信息，添加参数-m

		$ git commit -m [message]
	
	例如：git commit -m "第一次提交"
	
	跳过暂存，直接提交，添加参数-a

		$ git commit -am [message]
		
	3.6 删除文件
		1、从本地磁盘删除文件，同时删除git暂存区文件
		
		$ rm [files]
		$ git rm [files]
	
	2、保留本地磁盘文件，删除git暂存区文件，添加--cached参数
	
		$ git rm --cached [files]
		
	支持文件名匹配模式，即shell简化了的正则表达式（glob模式）
			1） 星号匹配零个或多个任意字符；
			2） [abc]匹配任何一个列在方括号中的字符；
			3） 问号?只匹配一个任意字符；
			4）  [0-9] 表示匹配所有 0 到 9 的数字。
			例如：删除log文件夹下的所有log后缀文件
				
		$ git rm log/\*.log
		
	注意：星号前有反斜杠
	3.7 移动文件
	可用于重命名文件
	
		$ git mv [file_from] [file_to]
	
	例如：git mv readme.txt readyou.txt
	3.8 查看提交历史
	
		$ git log

 4. 撤销操作
	 4.1 重新提交
	 
		$ git commit  --amend
		 
	 4.2 取消暂存文件
	 
		$ git reset HEAD [files]
	
	4.3 取消对文件的修改
	
		$ git checkout -- [files]

 5. 远程仓库操作
	5.1 添加远程仓库，并指定简写，默认简写为origin
	
		$ git remote add [shortname] [url]
	
	例如：
		
		git remote add my https://github.com/lishan666/git_tutor.git
	
	5.2 查看远程仓库信息
	
		 $ git remote -v
	 
	 5.3 拉取远程仓库信息，默认简写为origin
	
		$ git fetch [shortname]
	
	自动抓取远程分支，并后合并到当前分支，默认远程仓库的 master 分支

		$ git pull
		
	5.4 推送到远程仓库
	
		git push [remote] [branch]

	例如：将 master 分支推送到 origin 服务器，备份本地数据到远程服务器
	
		$ git push origin master

	注意：只有当你有所克隆服务器的写入权限，并且之前没有人推送过时，这条命令才能生效。
	

		
