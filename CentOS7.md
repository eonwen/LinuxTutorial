# 修改源，更新软件

```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo_bak # 备份本地 yum 源
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo # 获取阿里 yum 源配置文件
mv /etc/yum.repos.d/epel.repo /etc/yum.repos.d/epel.repo.bak
wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo
yum makecache # 更新缓存
yum -y update # 更新软件
```

# 用户相关操作

1. 注释掉不需要的用户和用户组

```bash
cp /etc/passwd /etc/passwd.bak # 备份
vi /etc/passwd # 在不需要的用户前 # 注释掉
cat /etc/passwd | grep -v /sbin/nologin | cut -d : -f 1 # 查看可以登陆系统的用户
passwd [user] # 修改用户密码
```

2. 创建用户并授权 `sudo` 权限

```bash
adduser username
passwd username
whereis sudoers # 查找文件位置
ls -l /etc/sudoers # 查看文件权限
chmod -v u+w /etc/sudoers # 修改文件权限为可编辑
vi /etc/sudoers #修改文件，添加 username ALL=(ALL) ALL
chmod -v u-w /etc/sudoers # 将文件还原为只读
```

3. 修改 root 密码

```bash
su root # 切换到 root 用户
passwd # 修改密码
```

# 修改 ssh 连接方式

1. 生成密钥对

```bash
ssh-keygen -t rsa # /root/.ssh
```

2. 将公钥制作成 key

```bash
mv id_rsa.pub authorized_keys
```

3. 修改公钥和私钥的权限

```bash
chmod 600 authorized_keys
```

4. 将私钥导入 `puttygen.exe` 保存为其可以识别的格式

5. 修改 `/etc/ssh/sshd_config` 文件，改变登陆方式

```bash
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication no
systemctl restart sshd
```

# 查看系统当前开启的服务，关闭无需服务

```bash
systemctl list-unit-files # 列出所有已经安装的服务及状态
systemctl enable postfix.service # 开机启用服务
systemctl disable postfix.service # 开机禁用服务
systemctl --failed # 查看启动失败的服务列表
```

# 安装 Python3

1. 安装依赖

```bash
yum install libffi-devel -y
yum install zlib zlib-devel -y
yum install openssl-devel -y
yum install sqlite-devel -y
```

2. 编译安装

```bash
./configure --prefix=/usr/local/python3 --with-ssl
make && make install
```

3. 建立软连接

```bash
rm /usr/bin/python # 删除已有软连接，否则无法覆盖
ln -s /usr/local/python3/bin/python3 /usr/bin/python # 建立软连接
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip # 建立软连接
```

4. 更换 `pip` 源

```
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
disable-pip-version-check = true
timeout = 6000
```

# 安装 `ftp`

1. 安装软件，注册服务并自动启用

```bash
yum install vsftpd -y # 安装
systemctl start vsftpd # 启动服务
systemctl enable vsftpd # 开机自启动
```

2. 配置防火墙

```bash
# 开放端口以便外部访问
firewall-cmd --zone=public --permanent --add-port=21/tcp
firewall-cmd --zone=public --permanent --add-service=ftp
firewall-cmd --reload
firewall-cmd --list-ports # 查看所有开放端口
```

3. 配置 FTP 服务器

```bash
cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.bak #备份

anonymous_enable=NO    # 禁用匿名登录
local_enable=YES       # 允许本地用户登录
write_enable=YES       # 允许对文件系统做改动的 FTP 命令
local_umask=022        # 本地用户创建文件所用的 umask 值
dirmessage_enable=YES  # 当用户首次进入一个新目录时显示一个消息
xferlog_enable=YES     # 用于记录上传、下载细节的日志文件
connect_from_port_20=YES # 使用端口 20 （ftp-data）用于 PORT 风格的连接
xferlog_std_format=YES # 使用标准的日志格式
listen=NO              # 不要让 vsftpd 运行在独立模式
listen_ipv6=YES        # vsftpd 将监听 IPv6 而不是 IPv4
pam_service_name=vsftpd #  vsftpd 使用的 PAM 服务名
userlist_enable=YES    # vsftpd 支持载入用户列表
userlist_file=/etc/vsftpd.userlist # 存储用户名的文件
userlist_deny=NO # 只有列表中的用户才能登陆
tcp_wrappers=YES       # 使用 tcp wrappers
chroot_local_user=YES # 用户可以设置 chroot jail，默认是登录后的家目录
allow_writeable_chroot=YES # 允许 chroot jail 目录可写

# 设置 SELinux 规则来允许 FTP 读取/写入用户的家目录
semanage boolean -m ftpd_full_access --on
systemctl restart vsftpd
```

4. 添加用户

```bash
echo "eonwen" | tee -a /etc/vsftpd.userlist
```

5. 配置不同的家目录

```bash
#allow_writeable_chroot=YES 不安全

# 为用户创建另一个替代根目录，并将所有用户对该目录的可写权限移除
mkdir /home/eonwen/ftp
chown nobody:nobody /home/eonwen/ftp
chmod a-w /home/eonwen/ftp
# 接下来，在用户存储他/她的文件的本地根目录下创建一个文件夹
mkdir /home/eonwen/ftp/files
chown eonwen:eonwen  /home/eonwen/ftp/files
chmod 0700 /home/eonwen/ftp/files/
# 在 vsftpd 配置文件中添加/修改这些选项
user_sub_token=$USER         ### 在本地根目录下插入用户名
local_root=/home/$USER/ftp   ### 定义任何用户的本地根目录
# 重启服务：
systemctl restart vsftpd
```

# 安装 `jupyter notebook`

1. 生成登陆密码

```python
from notebook.auth import passwd
passwd()
```

2. 准备启动配置文件

```bash
jupyter notebook --generate-config
# 文件地址：/home/eonwen/.jupyter/jupyter_notebook_config.py

c.NotebookApp.notebook_dir = '/home/git/jupyter/codes'
c.NotebookApp.port = 8888
c.NotebookApp.password = 'sha1:8ba6ed3ed711:8b9253b89af83513c9fe61bae8fbf2f3cd027a30'  # 这个就是我们上面生成的密码
c.NotebookApp.base_url = '/notebooks'
c.NotebookApp.port_retries = 50
c.NotebookApp.notebook_dir = '/home/musan/notebooks'
c.NotebookApp.open_browser = False
c.NotebookApp.allow_remote_access = True
```


3. 配置后台运行，开机自启动

```bash
# /home/eonwen/startups/notebooks.sh
#!/usr/bin/bash

/usr/bin/jupyter notebook

chmod +x notebooks.sh # 将其修改为可执行文件

# /etc/systemd/system/notebooks.service
[Unit]
Description=notebooks

[Service]
Type=simple
PIDFile=/run/notebooks.pid
ExecStart="/home/eonwen/startups/notebooks.sh"
User=eonwen
Group=eonwen
WorkingDirectory=/home/eonwen/notebooks/
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

4. 安装配置 `nginx`

```bash
yum install epel-release
yum install nginx
# 开放端口以便外部访问
firewall-cmd --zone=public --permanent --add-port=80/tcp
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --reload
```


5. 建立并编辑 `/etc/nginx/conf.d/jupyter.conf`

```bash
upstream notebook {
    server 127.0.0.1:8888;
}
server {
    listen 80;
    server_name 10.1.95.210;
    root /home/eonwen/notebooks

    location / {
        proxy_pass http://127.0.0.1:8888/notebooks;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Host $http_host;
        proxy_http_version 1.1;
        proxy_redirect off;
        proxy_buffering off;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_read_timeout 86400;
    }
}
```

# 安装 `mangodb`

1. 配置包管理系统

```bash
# 创建 /etc/yum.repos.d/mongodb-org-4.0.repo
[mongodb-org-4.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.0.asc
```

2. yum 安装

```bash
yum install -y mongodb-org
```

3. 开机自启动

```bash
systemctl start mongodb.server
systemctl enable mongodb.server
```

4. 创建用户

```mongo
use admin
db.createUser({
    user:"eonwen", pwd:"****",roles:[
        {role:"readWriteAnyDatabase", db:"admin"},
        {role:"userAdminAnyDatabase", db:"admin"}
    ]
})
```

(关于Linux 环境下Anaconda需要root权限的各种问题总结与解决)[https://blog.csdn.net/rainmaple20186/article/details/80664828]
(Centos7安装Miniconda及配置jupyter)[https://blog.51cto.com/loufeng/2342003]
(anaconda镜像不要再用清华的了)[https://blog.csdn.net/ddonking/article/details/82698151]
(centos查看系统/硬件信息及运维常用命令)[https://blog.csdn.net/zcyygyl/article/details/102504311]
(如何在 CentOS 7 中安装、配置和安全加固 FTP 服务)[https://linux.cn/article-8527-1.html?pr]
