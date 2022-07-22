# 部署Kubernetes Master

在master执行，使用的仓库为阿里云仓库

```bash
$ kubeadm init \
--apiserver-advertise-address=192.168.106.100 \
--image-repository registry.aliyuncs.com/google_containers \
--kubernetes-version v1.18.0 \
--service-cidr=10.96.0.0/12 \
--pod-network-cidr=10.244.0.0/16
```

使用kubectl工具：

```bash
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
$ kubectl get nodes
```

# 加入Kubernetes Node

在node种执行

向集群添加新节点后，执行在kubeadm init输出的kubeadm join

```bash
$ kubeadm join 192.168.106.100:6443 --token skpayc.wf1d6e1wyjbndzcx \
    --discovery-token-ca-cert-hash sha256:eec4ef8e55feba5976a4fe7fd7263ad27114ac56595dcf77c4f6b4398b418442 
```

默认token有效期为24小时，当过期之后，该token就不可用了。这时候就需要重新创建token，操作如下

```bash
kubeadm token create --print-join-command
```

# 部署CNI网络插件

```bash
wget https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```

默认镜像地址无法访问，sed命令修改为docker hub镜像仓库

``` bash
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

查看组件信息
kubectl get pods -n kube-system
```

# 测试kubernetes集群

在Kubernetes集群种创建一个pod，验证是否正常运行：

```bash
$ kubectl create deployment nginx --image=nginx
$ kubectl expose deployment nginx --port=80 --type=NodePort
$ kubectl get pod,svc
```

访问地址：http://NodeIP:Port

# 使用kubeamd方式搭建k8s集群

1. 安装三台虚拟机，安装操作系统centos7.x
2. 对三个安装之后的操作系统进行初始化设置
3. 在三个节点安装docker kubelet kubeadm kubectl
4. 在master节点执行kubeadm init命令进行初始化
5. 在node节点上执行kubeadm join命令把node节点添加到当前集群里面
6. 配置网络插件