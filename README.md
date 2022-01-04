# haha

##### 什么是Git
[[git]]的核心
- 仓库(repo) ：保存在项目目录下名为.git的隐藏子目录中。

- 提交 ：被添加到仓库(以数据库保存)的某个时间点的工作快照，或检查点
- 远程 ：指向非本机上仓库副本的链接。该链接指向了Web上副本存储的位置
- 合并：git支持多个不同版本的工作,所有版本并行存在着(在所谓的分支中)，这些版本可以由一个人或多个合作者创建。

GitHub是一个云托管项目副本的网站,支持多人协作(使用git)。git用来做版本控制；GitHub是一个可以用来保存代码仓库的地方。
##### 配置和项目设置
安装后第一次使用git，需要配置用户信息,以便你能够向仓库提交更改。
```shell
# Configure 'git' on your machine(only needs to be done once)

# Set your name to appear alongside your commits
#This *does not* need to be your GitHub username
git config --global user.name "YOUR FULLNAME"

# Set your email address
# This *does not* need to be the email associated with your GitHub accout

git config --globel user.email "YOUR_EMAIL_ADDRESS"

```
配置完成用户信息后,每天往GitHub提交代码仍旧需要输入密码，为GitHub设置一个SSH密匙可节省一些时间。

###### 生成一个仓库
```shell
# Create a new folder in your current location called `learning_git`
mkdir learning_git

# Change your current directory to the new folder you just created
cd learning_git

# Initialize a new repository inside your 'learning_git' folder
git init
```
git init 命令在当前目录新建了一个.git的隐藏文件夹。因为是隐藏的，查找器查不到该文件夹，但是用ls -a(带all参数的"list"命令)可看到。该文件夹是所作改动的“数据库”,git将保存这个文件夹中所有提交的改动。包含.git的文件夹会将一个目录转换成一个仓库,你可将整个目录称为“repo”
###### 检查状态
创建完repo后,下面将会介绍如何检查他的状态
```shell
# Check the status of your repository
#(this and other commands will only work inside git project folders)
git status
```
git status 命令将显示repo的状态。在一个新的repo上，执行该命令会列出下面的信息：
```shell
On branch master

No commits yet

nothing to commit(create/copy files and use "git add" to track)
```
在整个使用git过程中,git status是最有用的命令。在学习git基础知识时,在执行命令前后，查看一次项目更改状态是相当有用的。学习它，使用它，热爱它。

###### 添加文件
第一步是将这些改动添加到临时区域。临时区域就像在线商店的购物车：在更改记录提交到数据库之前(例如,在点击"购买"前),将改动放在临时存储区中。
```shell
# Add changes to a file with the name FILENAME to the staging area
# Replace FILENAME with the name of your file (e.g. books.txt)
git add FILENAME
```
这会将处于当前保存状态的单个文件添加到临时区域。如果以后改动该文件,需要再次运行git add命令添加文件的更新版本。
```shell
# Add all saved contents of the directory to the staging area
git add .


```
###### 提交
如果对临时区域的内容感到满意(即准备购买)，就到提交这些更改的时间了,将文件的快照保存到仓库数据库中。
```shell
# Create a commit(checkpoint) of the changes in the staging area
# Replace "Your message here" with a more informative message
git commit -m "Your message here"

```
###### 审核本地git流程
使用git的标准"开发循环"是编辑文件、添加文件、提交更改的循环
通常，代码要做大量改动(编辑大量文件、运行和测试代码等)，不过一旦有了好的“断点”,一旦要添加和提交更改,以确保工作不丢并能够随时回到这个“断点”位置。“断点”可以实现了一个功能、卡壳了需要喝咖啡了或是计划进行彻底更改。
<font color=#00FFFF>注意:</font>每次提交意味着一组改动,通常波及多个文件.不要一个文件的一次改动就提交一次;相反，每次提交应该是整个项目的快照
<font color=#00FFFF>技巧:</font>如果无意中添加了不想添加的文件,可通过git reset命令(没有参数)从临时区域中删除所有添加过的文件。
如果无意中提交了不想提交的文件,可使用git reset --soft HEAD~1撤销提交
