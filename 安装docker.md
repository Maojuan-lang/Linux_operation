# 安装docker

```bash
# 设置docker下载地址
$ wget https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo -O /etc/yum.repos.d/docker-ce.repo
# docker安装
$ yum -y install docker-ce-18.06.1.ce-3.el7
# 开机启动
$ systemctl enable docker && systemctl start docker
# 查看版本
$ docker --version
Docker version 18.06.1-ce, build e68fc7a
```

```bash
# 添加阿里云镜像
$ cat > /etc/docker/daemon.json << EOF
{
    "registry-mirrors": ["https://b9pmyelo.mirror.aliyuncs.com"]
}
EOF
# 重启docker服务
systemctl restart docker
```