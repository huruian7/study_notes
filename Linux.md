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
## 第二章 基本命令
### 2.1 特殊符号
```text
.  当前目录
..  上级目录
~   home目录
/   根目录
$   普通用户
#   root用户
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
### 2.4 touch-cat-more-tail
```shell
touch [文件名]
cat [路径]
```
2.5 grep wc


### 用户和用户组
```shell
useradd [-gdm] 用户名
1,-g代表指定路径
2，-d代表指定创建路径（默认在home目录下）
3，-m（如果在Ubuntu系统下，一定要加-m才会创建文件夹，否则只会有注册信息）

userdel [-r] 用户名
1，如果没有-r则不删除对应用户文件夹


```
su 切换用户
sudo
curl ifconfig.me  只显示ip
root@VM-0-5-ubuntu:~# cat /root/.openclaw/openclaw.json | grep -A2 token
      "mode": "token",
      "token": "2166d14cd969820a0c36d4bed4d846453bc066ded8356f56"
    },
    "tailscale": {