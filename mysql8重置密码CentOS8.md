# mysql8重置密码CentOS8

---

## 1. 跳过密码登陆

```py
# 在/etc/my.cnf文件中添加skip-grant-tables
# 例如[mysqld]
	  skip-grant-tables
```

---

## 2. 重启mysql

```py
# systemctl restart mysqld
# 若提示服务不存在，可使用chkconfig --list命令查看当前服务列表
```

---

## 3. 使用用户无密码登录

```pytho
# mysql
```

---

## 4. 选择数据库

```py
# use mysql;
```

---

## 5. 修改root密码

```py
# alter user 'root'@'localhost' identified by '我是密码';
# 若报错Operation ALTER USER failed for 'test'@'localhost'
# 则是进行了mysql8以前版本的操作导致password不为空（重置密码需置空）
# 使用以下命令置空password
# update user set authentication_string='' where user='root';
# 刷新权限
# flush privileges;
# 再次设置密码即可
# alter user 'root'@'localhost' identified by '我是密码';
```

---

## 6. 退出

```py
# 退出mysql
# quit;
```

---

## 7. 将第一步中添加到文件的skip-grant-tables删除

---

## 8. 重启mysql

```py
# service mysql restart
```

