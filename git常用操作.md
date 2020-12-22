#时间：2020年12月22日16:33:40
#作者：李珊
#内容：git的基本使用教程
#操作系统：Windows10

安装git，官网下载地址：

> [https://git-scm.com/download/win](https://git-scm.com/download/win)

 1. 基础配置
	1.1 配置用户名、邮箱（用于身份验证）

	    $ git config --global user.name [name]
	    $ git config --global user.email [email]

 2. 获取git仓库
	 2.1 创建一个本地仓库
	进入目标文件夹，初始化git仓库

	    $ git init
    
	2.2 从服务器克隆一个已存在的仓库

	    $ git clone [url]
    
	例如：git clone https://github.com/libgit2/libgit2
	
	自定义克隆的项目名，在末尾添加新的项目名称
	例如：git clone https://github.com/libgit2/libgit2 mylibgit
	
	备注：git支持https协议，也支持ssh协议
	例如：git clone git@github.com:lishan666/git_tutor.git
	
3. 文件操作
	 3.1 检查文件状态
		
	完整版
		
		$ git status
	
	简洁版，添加参数-s

		$ git status -s
	 
	 3.2 跟踪新文件，添加文件到暂存区，暂存已修改文件

		 $ git add [files1] [files2] [...]
	
	备注：可跟踪一个文件，多个文件或整个文件夹
		
	3.3 忽略文件
	创建一个名为 .gitignore的文件，列出要忽略的文件的模式
	
		$ cat .gitignore
		*.[oa]
		*~
 	第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。
 	 第二行告诉 Git 忽略所有名字以波浪符（~）结尾的文件
	此外，你可能还需要忽略 log，tmp 或者 pid 等目录。 
	
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
	
	跳过暂存，直接提交，添加参数-a

		$ git commit -am [message]
