git应用场景 : 云备份;分布式版本控制;协同开发

[[]]
## （一) git基本流程
### 1,1 配置
#### 1,1,1 用户配置:
```shell
1. git config --global user.name "用户名"
2. git config --global user.email "邮箱"
```
<div style="font-weight:bold;color:#d4a5a5">PS:user.name和email只是git版本署名，无其他作用</div>
#### 1,1,2 ssh密钥对配置:
```shell
1. ssh-keygen -t ed25519 -C ""
-t ed25519指定加密算法（如果考虑兼容性用RSA）
-C 注释
2. cat ~/.ssh/id_ed25519.pub（默认路径在~/.ssh下。Windows用type命令,但注意分隔符是\）
这里注意一把公钥完全可以粘贴到各平台，比如id_ed25519.pub可以放到Linux云服务器，也可以放到gitee/github平台上
3. 检测 SSH 密钥是否匹配成功
-T让 SSH 连接只做 “密钥认证”，不创建任何终端会话
```
![[ssh.png]]
### 1,2 创建本地及云端仓库
```shell
1. git init
初始化仓库（执行命令后当前目录会多出一个.git文件夹，这是git版本控制的核心）
2. 创建云端仓库
在gitee/github建立一个云端仓库，这里以gitee为例
3. git remote add origin git@gitee.com:hu-xiao-ding-dang/myproject.git
关联云端仓库。origin为云端仓库名，默认为origin（也可自由更改）;需要留意gitee.com后面是':'不要错写'/',最后要给仓库名加上.git后缀，表明为git项目。需要多提一点的是，关联远程仓库格式/地址写错了git不会报错，因为git只是让你给他指个路，但后续push会报错
```
<div style="font-weight:bold;color:#d4a5a5">PS: git init是git版本控制的核心，有这个隐藏的.git文件夹才会被git识别为git项目,所以执行git命令一定要在有.git的项目下，否则无效。其次仅仅靠git remote add origin关联gitee云仓库是连不上gitee的，还需要ssh</div>
### 1.3 push三部曲
```shell
1. git add .
把文件添加到暂缓区
2. git commit -m ""
提交到本地仓库，-m为注释
3. git push [远程仓库名] [主分支名]
提交到远程仓库
```
<div style="font-weight:bold;color:#d4a5a5">PS:可以结合git status命令观察其变动</div>
## (二) 常用命令
### 2,1 remote
```shell
1. git remote 
列出当前仓库关联的远程仓库名称
2. git remote -v
列出当前仓库关联的远程仓库名称+对应地址
3. git remote add [仓库名] 远程仓库地址
关联云端仓库
4. git remote set-url [原仓库名] 修改后的远程仓库地址
修改云端仓库地址。比如gitee远程仓库地址写错了，原仓库名就写gitee
5. git remote rename [原仓库名] [修改后仓库名]
修改云端仓库名称
6. git remote remove [要删除的仓库名]
删除云端仓库
```
### 2,2 branch
```shell
1. git branch
列出当前仓库分支名称
2. git branch -v
列出当前仓库名称及最后一次提交的哈希值及提交说明
3. git branch [分支名]
创建分支，一般主分支为master或main
4. git checkout/switch [分支名]
切换分支，switch是新版的指令
5. git branch -m [原分支] [改名后分支]
重命名分支(move,移动，在Linux中mv是不是也代表重命名)
6. git branch -d [分支名]
删除分支
7. git branch -a
8. git branch -r
   git branch -vv
```
<div style="font-weight:bold;color:#d4a5a5">PS:有没有人疑惑为什么branch是-m,-d；remote确是rename,remote。我们可以这样记忆，因为先有remote再有branch，那自然remote的选项必branch长咯</div>
### 2,3 pull
pull，顾名思义，从远程拉取代码。但它其实是git fetch（拉取远程代码到缓存，只读）和git merge（合并到工作区）的组合操作，这也就解释了为什么我们通过git remote -v看到的是fetch，push而不是pull,push了
```shell
1. git branch --set-upstream-to=[远程仓库名]/远程分支 本地分支
关联本地分支到远程分支
2. git pull
```
<div style="font-weight:bold;color:#d4a5a5">PS:特别注意，pull和push是两个完全独立的操作，不要认为push到远程仓库了，下次pull就可以自动从远程仓库拉代码。push不会自动关联（除非加了-u选项），所以我们需要显示地关联本地分支和远程分支</div>

git clone
git merge
冲突
git statusff
fetch和push

