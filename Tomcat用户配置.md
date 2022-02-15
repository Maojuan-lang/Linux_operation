# Tomcat添加用户和权限

---

## 1. 添加用户和权限

```py
# vim /opt/local/tomcat/conf/tomcat-users.xml
# 添加如下到文件中
'''
<tomcat-users>
      <role rolename="manager-script"/>
      <role rolename="manager-gui"/>
      <role rolename="manager-status"/>
      <role rolename="admin-gui"/>
      <role rolename="admin-script"/>
      <user username="tomcat" password="password" roles="manager-gui,manager-script,manager-status,admin-gui,admin-script"/>
</tomcat-users>
'''
# 权限说明
'''
权限说明
admin-gui — 可访问 "host管理" 页面，但"APP管理" 和 "服务器状态" 页面无查看权限
manager-gui — 无 "host管理" 页面访问权限，有"APP管理" 和 "服务器状态" 页面查看权限
manager-status — 只有"服务器状态" 页面查看权限
manager-script — 有脚本方式管理接口访问权限和"服务器状态" 页面查看权限
manager-jmx — JMX 代理接口访问权限和"服务器状态" 页面查看权限
admin-script — 只有host-manager脚本方式管理接口访问权限
'''
```

---

## 2. 修改访问ip配置

```py
# vim /opt/local/tomcat/webapps/manager/META-INF/context.xml
# 如果没有特殊需求，可以将如下两行注释掉
'''
<!--<Valve className="org.apache.catalina.valves.RemoteAddrValve"
    allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />-->
'''
```

---

## 3. 重启Tomcat

```py
# /opt/local/tomcat/bin/shutdown.sh # 停止
# /opt/local/tomcat/bin/startup.sh # 启动
```

