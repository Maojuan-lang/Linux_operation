# docker安装

---

## 1. 通过 uname -r 命令查看当前的内核版本

```py
# uname -r
```

---

## 2. 使用 root 权限登录 Centos，更新 yum 包

```py
# yum -y update
```

---

## 3. 卸载旧版本(如果安装过旧版本)
```py
# 卸载docker相关,可以通过yum list installed命令查看yum安装过的软件包
# yum remove docker docker-common docker-selinux docker-engine
```

---

## 4. 安装依赖软件包， yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的

```py
# yum install -y yum-utils device-mapper-persistent-data lvm2
```

---

## 5. 设置yum源

```py
# yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# 阿里源
# yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

---

## 6. 查看仓库中所有docker版本

```py
# yum list docker-ce --showduplicates | sort -r
```

---

## 7. 安装docker

```py
# sudo yum install -y docker-ce
# 由于repo中默认只开启stable仓库，默认安装最新稳定版，-ce表示免费版本，还有ee闭源版
# 安装特定版本例子：sudo yum install -y docker-ce-3:20.10.9-3.el8(版本号)
```

---

## 8. 启动docker和开机启动

```py
# 启动docker
# systemctl start docker
# 设置为开机启动
# systemctl enable docker
```

---

## 9.验证安装是否成功

```py
# 启动docker后可用如下命令查看
# docker version
# 有client和server表示docker安装启动都成功了
```

