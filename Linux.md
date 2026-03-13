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
su 切换用户
sudo
curl ifconfig.me  只显示ip
root@VM-0-5-ubuntu:~# cat /root/.openclaw/openclaw.json | grep -A2 token
      "mode": "token",
      "token": "2166d14cd969820a0c36d4bed4d846453bc066ded8356f56"
    },
    "tailscale": {