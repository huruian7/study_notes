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
```
### 1,2 创建本地及云端仓库
```shell
1. git init
初始化仓库（执行命令后当前目录会多出一个.git文件夹，这是git版本控制的核心）
2. 创建云端仓库
在gitee/github建立一个云端仓库，这里以gitee为例
3. git remote add origin git@gitee.com:hu-xiao-ding-dang/myproject.git
关联云端仓库。origin为云端仓库名，默认为origin（也可自由更改）;需要留意gitee.com后面是':'不要错写'/',最后要给仓库名加上.git后缀，表明为git项目
```
<div style="font-weight:bold;color:#d4a5a5">PS: git init是git版本控制的核心，有这个隐藏的.git文件夹才会被git识别为git项目。其次仅仅靠git remote add origin关联gitee云仓库是连不上gitee的，还需要ssh</div>
### 1.3 push三部曲
```shell
1. git add .
把文件添加到暂缓区
2. git commit -m ""
提交到本地仓库，-m为注释
3. git push [远程仓库名] [主分支名]
提交到远程仓库
```
