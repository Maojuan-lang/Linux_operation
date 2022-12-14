# Ubuntu安装docker

---

```
1. 查看系统内核
uname -a
2. 查看系统版本
lsb_release -a
3. 升级apt到最新版本
apt-update
4. 安装系统工具
apt -y install apt-transport-https ca-certificates curl software-properties-common
5. 安装gpg证书
((f连接失败时不显示http错误，s不显示失败信息和错误信息，S只显示错误信息，L跟随重定向跳转)(最后的-表示标准输入))
curl -fsSL https://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | apt-key add -
6. 写入阿里云镜像的源地址
(deb是二级制包仓库，[arch=amd64]框架是amd64，仓库url，$(lsb_release -cs)是bash命令，用于获取Ubuntu版本 stable表示的是稳定版)
add-apt-repository "deb [arch=amd64] https://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
7. 再次更新apt
apt update
8. 安装docker
apt -y install docker-ce
9. 测试docker命令
docker ps -a
```

