# Mysql8重置密码CentOS8

---

## 1. 跳过密码登陆

```py
# 在/etc/my.cnf文件中添加skip-grant-tables
# （一定要放到[mysqld]下面）
[mysqld]
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
# -- 查询一下安全模式开关
# show variables like 'sql_safe_updates';
# -- 关闭安全模式
# set sql_safe_updates = 0;
# -- 关闭安全模式下，才可以执行authentication_string为空
# update user set authentication_string='' where user='root';
# -- authentication_string空了的情况下，才可以真正修改密码
# -- 刷新权限表
# flush privileges;
# -- 根据下面查询，修改密码
# select user, host from user;
# -- 修改密码（下面为两个常见例子）
# alter user 'root'@'%' identified by 'maojuan';
# alter user 'root'@'localhost' identified by 'maojuan';
# -- 打开安全模式
# set sql_safe_updates = 1;
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

---

## 废案修改密码

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
