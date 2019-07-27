# 关机问题修正

1. 打开配置文件：`sudo vim /etc/systemd/system.conf`

2. 在最后新增两行内容

    `DefaultTimeoutStartSec=10s`

    `DefaultTimeoutStopSec=10s`

# 安装中文输入法

1. 下载安装包： `wget http://cdn2.ime.sogou.com/dl/index/1524572264/sogoupinyin_2.2.0.0108_amd64.deb?st=SPUNhfkbhLQ2dW1mkrv3WA&e=1564148153&fn=sogoupinyin_2.2.0.0108_amd64.deb`

2. 在软件仓库中安装 `fcitx`

3. 安装搜狗拼音

4. 重启系统