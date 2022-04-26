# Centos配置网络

---

## 1.找到配置文件
```py
# 进入/etc/sysconfig/network-scripts/文件夹
# 找到ifcfg-[网卡名]的文件
```

---

## 2.修改配置文件
```py
# 自动分配
# BOOTPROTO=hdfs
# ONBOOT=yes
# 静态
# BOOTPROTO=hdfs
# ONBOOT=yes
# IPADDR=xxx.xxx.xxx.yyy
# PREFIX=24
# GATEWAY=xxx.xxx.xxx.y
# DNS1=
```

---

## 3.重启网络服务
```py
# 重启网络服务
# sytemctl restart network
```
