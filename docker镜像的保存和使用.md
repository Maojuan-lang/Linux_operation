# docker镜像的保存和使用

---

```
只把镜像当前的状态保存下来，没有历史版本等信息，文件比较小
xxx表示image的md5
docker export xxxxxxxxxx -o nginx.tar
save命令会将镜像完整保存，包括历史版本和元数据信息，所以文件可能比较大
docker save xxxxxxxxxx -o nginx.tar
导入镜像
docker load -i nginx.tar
如果报错open /var/lib/docker/tmp/docker-import-970689518/bin/json: no such file or directory，可使用如下命令导入
cat nginx.tar | docker import - nginx
用镜像新建一个容器
docker run --restart=always --name=nginx -p 2333:80 qinglong:latest /bin/bash

```

