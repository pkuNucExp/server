<!-- Setup28.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 六 8月 31 14:49:11 2019 (+0800)
;; Last-Updated: 日 9月  1 17:28:46 2019 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 10
;; URL: http://wuhongyi.cn -->

# README

## yum 软件安装

```bash
# emacs
sudo yum install emacs
```

## 网络代理配置

开放端口
```bash
sudo sudo firewall-cmd --permanent --zone=public --add-port=3128/tcp
sudo firewall-cmd --reload
```


安装squid
```bash
sudo yum install squid
```

cd  /etc/squid/ 目下， 修改squid.conf 文件中的内容，修改之前， 可以先备份该文件：
```bash
cp squid.conf squid.conf_bak
```

然后找到 文件中的 **http_access deny all**   将其修改为 **http_access allow all**  表示所有用户都可以访问这个代理，还有找到  **http_port 3128**  修改为  **http_port xxx.xxx.xxx.xxx:3128**  这里的IP及端口是squid的代理IP及端口，该IP是能访问外网机器的IP地址，如果是本机，则可以不用修改该地址，

```bash
#添加以下信息
#防止被人利用为HTTP代理，设置允许访问的IP地址                                   
acl myip dst 162.105.151.64
acl myip dst 162.105.151.30
http_access deny !myip


#开启以下
cache_dir ufs /var/spool/squid 100 16 256
```

下面启动squid 代理

```bash
squid -k parse
squid -z
service squid start

#设置开机启动
systemctl enable squid

##可用一下命令查看端口开启情况
netstat -nltp
```




## 错误操作记录

```bash
<!-- restorecon -FvR /path/to/your/wiki -->
<!-- setsebool -P httpd_unified 1 -->
<!-- setsebool -P allow_httpd_anon_write 1 -->
```


<!-- Setup28.md ends here -->
