<!-- Setup64.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 二 8月  6 17:10:20 2019 (+0800)
;; Last-Updated: 二 1月 26 22:07:39 2021 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 22
;; URL: http://wuhongyi.cn -->

# 64服务器管理员配置

## 硬件信息

* DELL PowerEdge R940xa 4U机架式服务器
  * CPU：4颗Intel Xeon Gold 6136 （3.0GHz/12C/24.19.25M Cache）
  * 内存：128GB RDIMM，速度高达 2933 MT/s
  * 硬盘：2个600GB 10K RPM SAS 12Gbps 512e 2.5英寸热插拔硬盘 
  * 网卡：Network Options 4 GbE端口 + 2个10GbE（配齐全光模块）
  * 阵列卡：PERC H730P RAID 控制器，2GB NV 缓存
  * 电源：多个冗余热插拔电源1100W 
  * 配件：配置原装导轨； 
* 100T磁盘阵列升级万兆光纤模块明细：
  * 四合一光纤通道子板9200*2=18400
  * 4个万兆多模4*850=3400
  * 4条3米LC-LC线100*4=400
  * 双口万兆卡4200
  * 合计：26400

## 保留端口

- 61208 glances
	- 访问模式 http://xxx.xxx.xxx.64:61208/


## port 端口开放

jupyter 已分配端口号

- 8888 默认端口，请不要长时间占用
- 8900/8901 武晨光
- 8902/8903 金瑜
- 8904/8905 王翔
- 8906/8907 韩家兴
- 8908/8909 李根
- 8910/8911 吴鸿毅
- 8912/8913 陈家豪
- 8914/8915 李智焕
- 8916/8917 郭成宇
- 8918/8919 周振翔
- 8920/8921 陈莹
- 8922/8923 朱宏渝
- 8924/8925 胡梓瑶


```bash
#端口分配,将 xxxx 替换成端口号
sudo firewall-cmd --permanent --zone=public --add-port=xxxx/udp
sudo firewall-cmd --permanent --zone=public --add-port=xxxx/tcp

# 使最新的防火墙设置规则生效
sudo firewall-cmd --reload
```



## yum 程序安装

YUM 源配置  /etc/yum.repos.d

```bash
yum install environment-modules

#多机并行（G4的多机并行）
yum install mpich-3.2.x86_64 mpich-3.2-devel.x86_64


#screen
yum install screen.x86_64

#自动输入密码
yum install sshpass.x86_64

#shell脚本加密
yum -y install shc.x86_64


#打开ntfs/exfat格式硬盘
yum install findntfs.x86_64 ntfs-3g.x86_64 ntfs-3g-devel.x86_64
yum install fuse-exfat.x86_64 exfat-utils.x86_64

#hdf5
yum install hdf5.x86_64  hdf5-devel.x86_64 hdf5-mpich.x86_64 hdf5-mpich-devel.x86_64  hdf5-openmpi.x86_64 hdf5-openmpi-devel.x86_64

#UnitTest++
yum -y install unittest-cpp.x86_64 unittest-cpp-devel.x86_64


#python3
yum install python36.x86_64 python36-devel.x86_64 python36-libs.x86_64 python36-tkinter.x86_64 python36-pip.noarch python36-cffi.x86_64 python36-cryptography.x86_64 python36-cryptography-vectors.noarch python36-decorator.noarch python36-idna.noarch python36-ipython_genutils.noarch python36-ply.noarch python36-pyasn1.noarch python36-pycparser.noarch python36-six.noarch python36-traitlets.noarch python36-mysql.x86_64 python36-jinja2.noarch


#clang编译器
yum install clang.x86_64 clang-devel.x86_64

# ROOT
yum install lz4-devel.x86_64 ruby-devel.x86_64 expect-devel.x86_64  glew.x86_64 gsl-devel.x86_64 libxml2-static.x86_64 R.x86_64 R-RInside.x86_64 R-RInside-devel.x86_64 R-Rcpp.x86_64 R-Rcpp-devel.x86_64 cfitsio.x86_64 cfitsio-devel.x86_64 davix.x86_64 davix-devel.x86_64 ftgl.x86_64 ftgl-devel.x86_64 gfal2.x86_64 gfal2-all.x86_64 gfal2-devel.x86_64 mysql++.x86_64 mysql++-devel.x86_64 pythia8.x86_64 pythia8-devel.x86_64 unuran.x86_64 unuran-devel.x86_64 xrootd.x86_64 xrootd-client.x86_64 xrootd-client-devel.x86_64 xrootd-devel.x86_64

#moin
yum install httpd mod_wsgi

#TeamViewer
yum -y install qt5-qtwebkit.x86_64 qt5-qtwebkit-devel.x86_64
```


## SSH 服务安全设定

sshd 的安全是指它在 Internet 上传递的数据是加密的，但 sshd 服务本身并不那样安全。sshd 安全设定从以下几个方面来进行：
* 强化服务器软件本身的设定：/etc/ssh/sshd_config
  * 禁止 root 和 nossh 群组用户使用 sshd 的服务；
* 启动 ssh 服务在非正规端口，而非默认端口 22：很多 cracker 会使用扫描程序乱扫整个 Internet 的埠口漏洞，port 22 就是一个常被扫描的端口
* TCP wrapper 的使用
  * 只让本机以及区网内的主机来源通过 sshd 登入
* Firewalld 的使用
  * 取消端口 22 的放行，指定 IP 访问 ssh 开启的非正规端口



<!-- Setup64.md ends here -->
