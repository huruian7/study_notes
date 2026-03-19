发明git和代理的真的是天才!!!

squid:一台长期运行在 Linux 上的中间转发程序

## 【第一步：在 香港服务器 上执行】

### 1. 安装 squid 代理
```shell
apt update && apt install squid
```
### 2. 备份原配置（好习惯）
```shell
cp /etc/squid/squid.conf /etc/squid/squid.conf.bak
```