## 第一章 简单介绍
1. Linux操作系统=内核+系统级应用程序
2. Linux发行版：由于代码开源，提供内核+系统级应用程序封装的软件就是Linux发行版，有多个发行版，常用的是Ubuntu和CentOS
3. 安装Linux通常有四种途径：
	- 虚拟机
	- WSL
	- 云服务器
	- 双系统
4. SSH远程连接（FinalShell）：ssh 远程服务器用户名@ip地址
5. /   Linux,网址；   \   Windows
6. Linux区分大小写
7. 选中复制，右键粘贴
8. ssh和mosh
- ssh是TCP连接
- mosh是UDP连接
## 第二章 基本命令
### 2.1 特殊符号
```text
.  当前目录
..  上级目录
~   用户目录
/   根目录
$   普通用户（写在变量前表示取值）
#   root用户

·· 反引号（被包裹的内容将作为命令执行）
>  重定向（覆盖）
>> 重定向（追加）
```
### 2.2 ls
```shell
ls [-alh] [路径]

1，没有路径参数，则平铺显示
2，-a显示所有文件（包含隐藏）
3，-l以列表形式显示
4，-h配合-l选项使用,以更人性化的方式展示信息
```
### 2.3 cp-mv-rm
```shell
cp/mv/rm [-rf] [源路径] [目标路径]
作用对象为文件/目录，目录需要-r迭代选项
```
### 2.4 mkdir-touch-cat-more-tail
```shell
mkdir 目录
touch [文件名]
cat [路径]
more  可翻页查看
tail  从尾部查看
```
### 2.5 grep wc
```shell
grep 过滤
wc 统计
```
### 2.6 which find
```shell
which
find
```
### 2.7 echo
```shell
显示终端内容，用反引号包裹可以作为命令被执行
1，配合重定向符把内容写入文件
echo "hello" > test.txt
echo "hello" >> test.txt
2,取变量的值,可拼接文件名/路径（一般出现在shell脚本中）
name=hrx
echo "name:$name"
3,配合反引号作为命令执行
echo `date`
```
### 2.8 vim编辑器
```shell
vim有三种编辑模式，默认进入命令模式（还有插入模式，底线命令模式）
注意一定要用英文输入法，否则会没反应
```
#### 2.8.1 命令模式
```shell
1，dd 删除光标所在行
2，ndd 光标向下删除n行
3，yy 复制光标所在行
4，nyy 光标向下复制n行
5，u 撤销（ctrl+r 反向撤销）
6，gg 光标跳到首行
7，G 光标跳到行尾
8，dgg 删除当前光标到首行的所有行
9，dG 删除当前光标到行尾的所有行

/ 搜索模式
输入检索信息enter，n表示下一个，N表示上一个
```
#### 2.8.2 插入模式
```shell
1. i  进入插入模式
2. ESC 退出插入模式
3. /   搜索
```
#### 2.8.3 底线命令模式
```shell
1. :  进入底线命令模式
2. wq  保存退出
3. q!  强制退出
4. set nu 显示行号
5. set paste 原样粘贴(set nopaste)
```
## 第三章 用户
### 3.1 用户和用户组管理
#### 3.1.1 su和sudo
```shell
普通用户权限：仅可以在home目录操作
1，sudo可以为用户提权（但需要输入密码）
2，su是切换用户，不写用户名切换为root
ps：但一般用exit切换用户，因为su是打开一个子进程套娃
```
#### 3.1.2 sudo配置
```shell
sudo并不是所有用户都有权使用，需要进行配置(下面以test用户为例)
1，visudo /etc/sudoers
2，写入test ALL=(ALL:ALL) NOPASSWD:ALL

ps:切勿用vim编辑，要用visudo，执行这个命令系统会打开nano安全编辑（会自动识别是否写入错误，如果错误回退）
```
#### 3.1.3 添加/删除用户
```shell
useradd [-gdm] 用户名
1,-g代表指定路径
2，-d代表指定创建路径（默认在home目录下）
3，-m（如果在Ubuntu系统下，一定要加-m才会创建文件夹，否则只会有注册信息）

userdel [-r] 用户名
1，如果没有-r则不删除对应用户文件夹

ps:ubuntu有一个关于创建用户的adduser命令（引导模式），建议使用
```
#### 3.1.4 添加/删除用户组
```shell
groupadd
groupdel

getent passwd 查看Linux系统所有用户信息
getent group  查看用户组
ps:也可以去/etc/shadow查看密码（但这是加密的），去/etc/group去查看用户组信息
```
#### 3.1.5 Linux远程连接
```shell
场景:有时候ssh远程连接输对了密码还是显示permision denied，是因为系统设置了登录权限
getent passwd可以查看每个用户最后一段信息
bash（可以登录）
nologin（不允许登录，会弹出permission denied）
false（不允许登录，什么都不干）
```
### 3.2 权限信息
```shell
r 可读（4）
w 可写（2）
x 可执行（1）

比如-rw-rwx--x可以三三一组（除去第一个）
第一个字符代表当前文件类型，-代表文件，d代表目录，l代表软连接
rw-  表示所属用户权限
rwx  表示所属用户组权限
--x  表示其他用户权限
```
### 3.3 chmod
```shell
只有文件/文件夹所属用户或root可以用此命令
chmod -R u=rwx,g=rwx,o=rwx test.txt
其中-R表示如果在目录下执行则目录内的所有文件也会被迭代执行该命令，u，g,o分别代表用户，用户组，其他用户

```