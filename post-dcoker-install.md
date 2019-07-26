### 安装
在manajro下直接yaourt docker 
### 使用普通用户运行docker
Docker守护程序绑定到Unix套接字而不是TCP端口。默认情况下，Unix套接字由用户root拥有，而其他用户只能使用sudo访问它。
Docker守护程序始终以root用户身份运行。
如果您不想在docker命令前加上sudo，请创建一个名为docker的Unix组并向其添加用户。
当Docker守护程序启动时，它会创建一个可由docker组成员访问的Unix套接字。
执行下面语句就好。
```
sudo groupadd docker
sudo usermod -aG docker $USER
```
重新登录或者重启后生效，或者在当前终端生效执行
```
newgrp docker
```
### 更换镜像源
有时候使用官方镜像会各种报网络的错误。
创建或修改/etc/docker/daemon.json文件加入下面语句
```
{
    "registry-mirrors":["https://docker.mirrors.ustc.edu.cn"]
}
```
### 配置好上面的内容后就启动镜像

```
sudo systemctl start(或enable开机自启动)docker
```
如果要更改docker的dns的话，执行
```
sudo systemctl edit docker.service
然后添加
{"dns" : ["8.8.8.8","8.8.4.4"]}
然后执行
sudo systemctl daemon-reload
sudo systemctl restart docker
```

### 退出容器单不关闭
```
ctrl+p+q
```


## 参考资料
```
https://docs.docker.com/engine/reference/run/
https://docs.docker.com/install/linux/linux-postinstall/
```


