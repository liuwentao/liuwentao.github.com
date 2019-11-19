
## 前言

昨天因为帮一同事弄点东西，把自己用了两年多的一个nginx配置文件给删除了。。。主要是一些反代的配置。面临两个选择，要么用`nginx`重写，要么换其他的。候选的两个是[caddy](https://caddyserver.com)和[traefik](https://traefik.io/)。最终选了`caddy`

## 安装和配置

### 安装caddy

```bash
curl https://getcaddy.com | bash -s personal
```

### 新增用户

新增一个用户`caddy`。同时将用户目录指向`/var/www`

```
sudo adduser -r -d /var/www -s /sbin/nologin caddy
```

### 配置文件夹权限

```bash
sudo mkdir /etc/caddy
sudo chown -R root:caddy /etc/caddy
sudo touch /etc/caddy/Caddyfile
sudo mkdir /etc/ssl/caddy
sudo chown -R caddy:root /etc/ssl/caddy
sudo chmod 0770 /etc/ssl/caddy
sudo mkdir /var/www
sudo chown caddy:caddy /var/www
```

### 安装caddy服务

```bash
sudo curl -s https://raw.githubusercontent.com/mholt/caddy/master/dist/init/linux-systemd/caddy.service -o /etc/systemd/system/caddy.service
```

修改服务启动用户名

```bash
sudo vi /etc/systemd/system/caddy.service
```
将其中的`www-data`替换成`caddy`
```ini
; User and group the process will run as.
User=www-data
Group=www-data
```

重新加载下服务，并启用`caddy`服务

```bash
sudo systemctl daemon-reload
sudo systemctl enable caddy.service
```

### 开启防火墙

```bash
sudo firewall-cmd --permanent --zone=public --add-service=http 
sudo firewall-cmd --permanent --zone=public --add-service=https
sudo firewall-cmd --reload
```

### 修改配置文件

配置文件的位置在`/etc/caddy/Caddyfile`
```conf
http://a.test.com {
root /var/www
}
```

这样就搭建好了一个`caddy`服务。然后启动服务

```bash
sudo systemctl start caddy
```

如果要做反代的话，可以做如下的配置

```
https://a.test.com {
gzip
tls  youname@mail.com
proxy / http://127.0.0.1:7788 {
        transparent
}
}
```

其中比较关键的配置项就是`transparent`。这个代表了如下的配置：

```****
header_upstream Host {host}
header_upstream X-Real-IP {remote}
header_upstream X-Forwarded-For {remote}
header_upstream X-Forwarded-Port {server_port}
header_upstream X-Forwarded-Proto {scheme}
```
这个配置简直就是为做反代准备的。