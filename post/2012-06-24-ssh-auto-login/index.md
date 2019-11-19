
### 自动ssh/scp方法

A为主机; B为远程主机, 假如ip为192.168.1.102; A和B的系统都是Linux

在A上运行命令:

```bash
ssh-keygen -t rsa (按照提示操作就可以了)
ssh root@192.168.1.102 "mkdir .ssh"
scp ~/.ssh/id<em>rsa.pub root@192.168.1.102:.ssh/id</em>rsa.pub
```
  
在B上的命令:

```bash
touch /root/.ssh/authorized_keys （认证key，可以存放多个）
cat /root/.ssh/id<em>rsa.pub >> /root/.ssh/authorized_keys (将id<em>rsa.pub的内容追加到authorized</em>keys 中)
```

回到A机器:

> ssh root@192.168.1.102 (不需要密码, 登录成功)