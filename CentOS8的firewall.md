# Firewall

---

## 1. 防火墙开机启动 

```py
# systemctl enable firewalld.service
```

---

## 2. 查看防火墙状态

```py
# firewall-cmd --state
```

---

## 3. 开放8080端口

```py
# firewall-cmd --zone=public --add-port=8080/tcp --permanent
# （--permanent永久生效，没有此参数重启后失效）
# 关闭端口
# firewall-cmd --remove-port=8080/tcp --permanent
# 这些完成需要重新加载配置（步骤5）
```

---

## 4. 重启防火墙

```py
# systemctl restart firewalld.service
```

---

## 5. 防火墙重新加载配置

```py
# firewall-cmd --reload
```

---

## 6.查看开放的端口

```py
# firewall-cmd --list-ports
```

