# 第一章 AList+IDM-Activation-Script无限续杯
1. AList负责获取直链地址，idm负责下载，iac负责无限续杯（都需要先从github那里下载，idm官网下载）
2. IDM-Activation-Script负责清空本机idm的注册信息（右击运行脚本文件即可）
```
idm设置：
	用户代理设置为netdisk     //将下载请求伪装成百度官方行为
	默认最大连接数改为32      //提升速度

如果idm过期了，重新以管理员身份运行IAS（汉化）.cmd
```
```
Alist设置：
	以管理员身份运行Alist.exe(运行完的cmd窗口不能关)
	账号admin；密码Hh……z
	登录网站http://127.0.0.1:5244/（不知道后面会不会变）
	AList怎么配置的可以参考github具体教程
	
	- **网盘（如百度网盘）**：就像是远在云端的“水厂”，你平时必须打开浏览器或 App 才能看到里面的水（文件）。
    
- **挂载**：就是在你自己的电脑（AList）和云端网盘之间**接通一根水管**。
    
- **结果**：挂载成功后，你不需要打开网盘 App，直接通过 AList 这个“水龙头”就能管理、查看或下载云端的所有文件
```

# 第二章 Clash Verge+Antigravity tool额度监控
1. github上安装clash verge，开全局，tun模式
2. Antigravity tool解决谷歌账号无资质问题

# 第三章 Obsidian+Git本地云端同步存储
## 3.1 官网下载obsidian和git
方法一：插件Git，可以自动提交同步
方法二：在本地文件夹目录下输入cmd
```bash
git add .                               //把该目录下的所有文件都添加到箱子里
git commit -m "新增了JavaScript修炼文件"  //-m是告诉git这次提交的注释，必须有，方便回溯
git push origin JavaScript              //origin是远程仓库代号，JavaScript是当前分支

补充：
git init   把普通的文件夹变为受git保护的文件夹
git status 可以看当前的状态（发生了哪些变化）


如果连接github失败
#### ⚠️ 网络连接排错 (Port 443)
1. **排查端口**：通过 `系统设置 > 代理` 查看。
2. **确认监听**：使用 `netstat -ano | findstr "LISTENING"` 确认端口号（如 10810）是否活动。
3. **配置 Git**：
   - 开启代理：`git config --global http.proxy http://127.0.0.1:10810`
   - 关闭代理：`git config --global --unset http.proxy`
```

## 3.2 obsidian快捷键
1. ctrl家族
	- ctrl+数字  切换标题
	- ctrl+p     打开命令面板    
	- ctrl+l     无序列表/有序列表/待办
	- ctrl+e     切换编辑/阅读模式
2. 符号
	- [[]]       输入双中括号可以链接另一份笔记

## 3.3补充知识
- 127.0.0.1代表本机，别名为localhost
- 端口，一台电脑有很多端口，把ip想像为一个房子，那每个端口就是房子里的一个房间