# 利用Dockerfile自动创建sshd连接
1. 下载基础镜像
```php
$ docker pull ubuntu:18.04
```

2. 生成秘钥(如果存在,则省略这步)
```php
$ ssh-keygen -t rsa
```

3. 将秘钥内容重定向到authorized_keys文件
```php
$ cat ~/.ssh/id_rsa.pub > authorized_keys
```

4. 创建镜像
```php
$ docker build -t sshd:dockerfile .
```

5. 运行容器
```php
$ docker run -d -p 10122:22 sshd:dockerfile
```

6. 尝试连接(本机)
```php
$ ssh root@localhost -p 10122
```
