Windows操作系统必备技能
命令窗口（Command Prompt）或 PowerShell 操作

题外话
notepad++编辑器下载地址：https://notepad-plus-plus.org/downloads/
参考资料：
git官方教程中文文档 https://git-scm.com/book/zh/v2
Git教程 - 廖雪峰的官方网站 https://www.liaoxuefeng.com/wiki/896043488029600
Git 教程 | 菜鸟教程 https://www.runoob.com/git/git-tutorial.html
Git快速入门 - Git教程™ https://www.yiibai.com/git/git-quick-start.html
名词解释：
工作区：本地文件目录
版本库：本地文件目录里的.git隐藏文件夹，包括stage暂存区、master分支，指向master的第一个指针HEAD
暂存区：版本库里的stage（暂存区）
git add：将本地文件添加到暂存区
git commit：将暂存区文件添加到master分支

正式介绍
git的使用方法介绍

第一步：安装git
官网下载地址：https://git-scm.com/downloads
2.29.2 (2020-10-29)
windows：下载安装包直接安装
linux：sudo apt-get install git

第二步：创建版本库（仓库）
进入指定目录，右键打开Bash，初始化仓库
git init
会生成一个隐藏的.git目录

第三步：配置用户名、邮箱（用于身份验证）
git config --global user.name [name]
git config --global user.email [email]
说明：name 为用户名，email为邮箱，作为后续提交版本的身份验证信息
      global为全局配置，若不加此参数，设置只对本仓库有效
	  全局配置成功后，以后提交版本可不再重复配置
例如：
git config --global user.name "lishan666"
git config --global user.email "1624693146@qq.com"

第四步：添加文件
可添加单个文件、多个文件，也可添加整个文件夹
git add [file1] [file2] [file3] [file4]...
说明：file为文件全名，带后缀
例如：git add readme.txt

第五步：提交文件
一次性提交刚才添加的所有文件
git commit -m [messgae]
说明：-m表示参数message，后面的双引号内容为本次提交的说明信息
例如：git commit -m "first commit file"

若不想重复使用add命令添加文件，当文件修改后直接进行提交，可增加参数a，使用如下命令
git commit -am [messgae]

第六步：查看文件状态（最新提交new file、提交后又修改modified、新增文件但未添加Untracked、删除deleted、文件无任何修改clean）
查看当前仓库被修改文件：
git status
查看被修改内容
git diff
查看工作区和版本库里面最新版本的区别
git diff HEAD -- [file]
例如：git diff HEAD -- readme.txt

第七步：查看提交日志
查看每次提交版本、作者、时间、提交信息
git log
添加参数--pretty=oneline可简化输出信息
git log --pretty=oneline



撤销在工作区所做的修改：
git checkout -- [file]
例如：git checkout -- readme.txt

撤销在暂存区所做的修改，重新放回工作区：
git reset HEAD [file]
例如：git reset HEAD readme.txt

撤销在版本库的修改，版本回退
git reset --hard [commit_id]
说明：commit_id为版本号，当前版本号为HEAD^，上一个版本号为HEAD^^,上100个版本为HEAD~100
例如：git reset --hard HEAD^

查看历史命令
git reflog


删除文件
git rm [file]
例如：git rm test.txt

从版本库恢复文件
git checkout -- [file]
例如：git checkout -- test.txt

SSH方式关联远程仓库
git remote add origin [ssh_address]
例如：git remote add origin git@github.com:lishan666/git_tutor.git

HTTPS方式关联远程仓库
git remote add origin [https_address]
git remote add origin https://github.com/lishan666/git_tutor.git


推送本地库master分支到远程库master分支（关联master）
第一次推送：git push -u origin master
以后推送：git push origin master

查看git配置信息
git config --list


生成ssh秘钥方法：
检查是否存在ssh：
ls -al ~/.ssh

是否存在以下文件：
id_rsa.pub
id_ecdsa.pub
id_ed25519.pub
生成ssh秘钥：

ssh-keygen -t rsa -C [email]
-t 指定密钥类型，默认是 rsa ，可以省略
-C 设置注释文字，比如邮箱
-f 指定密钥文件存储文件名
例如：ssh-keygen -t rsa -C "1624693146@qq.com"
按3个回车，得到秘钥文件：
id_rsa（私有秘钥）和id_rsa.pub（公有秘钥）

cd ~/.ssh
cat id_rsa.pub
复制公有秘钥内容，登录github账号，点击右上角头像，选择settings->SSH and GPG keys->New SSH key,粘贴秘钥，输入秘钥名
测试：ssh -T ssh -T git@github.com








