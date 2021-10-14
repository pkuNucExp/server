<!-- Setup64.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 二 8月  6 17:10:20 2019 (+0800)
;; Last-Updated: 五 9月 17 21:38:09 2021 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 25
;; URL: http://wuhongyi.cn -->

# 64服务器管理员配置

## 硬件信息

* DELL PowerEdge R940xa 4U机架式服务器
  * CPU：4颗Intel Xeon Gold 6136 （3.0GHz/12C/24.19.25M Cache）
  * 内存：128GB RDIMM，速度高达 2933 MT/s
  * 硬盘：2个600GB 10K RPM SAS 12Gbps 512e 2.5英寸热插拔硬盘。另可加装 6 块 SAS 或 SATA 接口 2.5寸硬盘 SSD 或 HDD，现最大 2.5 寸 SAS 接口 HDD为 2.4 TB，最大 2.5 寸 SATA 接口 HDD为 2 TB
  * 网卡：Network Options 4 GbE端口 + 2个10GbE（配齐全光模块）
  * 阵列卡：PERC H730P RAID 控制器，2GB NV 缓存
  * 电源：自带多个冗余热插拔电源1100W，后更换为更大功率电源
  * 配件：配置原装导轨
  * 售后联系人：黄晓芬 18600634788；DELL 4008868618 白金服务，转接工程师
  * SN号 (戴尔服务编号)：F8RJ4Y2
  * 仪器编号：201913116
  * 室系号：000043301903
* 100T磁盘阵列升级万兆光纤模块明细：
  * 四合一光纤通道子板9200*2=18400
  * 4个万兆多模4*850=3400
  * 4条3米LC-LC线100*4=400
  * 双口万兆卡4200
  * 合计：26400
  * 售后联系人：唐尊龙（13552981464、微信号tzlxj1168）
  * ![image-20211014200059236](img/image-20211014200059236.png)

## 保留端口

- 61208 glances
	- 访问模式 http://xxx.xxx.xxx.64:61208/


## port 端口开放

jupyter 已分配端口号

- 8888 默认端口，请不要长时间占用
- 8900/8901 武晨光
- 8902/8903 金瑜
- 8904-8909 韩家兴
- 8910/8911 吴鸿毅
- 8912/8913 陈家豪
- 8914/8915 李智焕
- 8916/8917 郭成宇
- 8918/8919 周振翔
- 8920/8921 陈莹
- 8922/8923 朱宏渝
- 8924/8925 胡梓瑶
- 8926/8927 张集智
- 8928/8929 倪磊
- 8930/8931 张思洋


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


yum install telnet.x86_64
```

## 外挂磁盘阵列相关设定

### 开机后自动挂载

开机流程中/etc/fstab的执行在网络服务启动之前，因此无法利用其开机自动挂载磁盘阵列。sleep 10s也是为了确保网络服务完全启动之后才去挂载磁盘阵列。

```bash
[root~]# vi /etc/rc.d/rc.local (在最后加入以下几行)
sleep 10s && mount -t xfs UUID=a9c5eb55-d3dd-4b74-bfad-3ee4734ebe81 /data/d1 &
sleep 10s && mount -t xfs UUID=7e5ff28b-3d14-40a6-8c5b-eac71b4cf2ed /data/d2 &
sleep 10s && mount -t xfs UUID=39b59495-97eb-4f56-ad0e-10309c3aa4c0 /data/d3 &
# linux根据开机检测顺序来命名磁盘sda,sdb,…
# USB设备会最先被检测到而被命名为sda，系统盘和数据盘则顺延。所以尽量不要用sda，而是用UUID或挂载目录.
```

### 关机前卸载

#### 关机前自动卸载磁盘阵列

* 创建systemd服务

  ```bash
  [root@www ~]# vi /usr/lib/systemd/system/stopSrv.service
  [Unit]
  Description=close services before reboot and shutdown
  DefaultDependencies=no
  Before=shutdown.target reboot.target halt.target
  # This works because it is installed in the target and will be
  #   executed before the target state is entered
  # Also consider kexec.target
  
  [Service]
  Type=oneshot
  ExecStart=/root/bin/umountRAID  #your path and filename
  
  [Install]
  WantedBy=halt.target reboot.target shutdown.target
  ```

* 开机自启动服务

  ```bash
  [root@www ~]# systemctl enable stopSrv
  ```

* 编写运行脚本

  ```bash
  [root@www ~]# vi /root/bin/umountRAID
  #!/bin/bash
  #This script is added to /usr/lib/systemd/system/stopSrv.servic and will be executed before shutdown.
  
  fuser -ck /data/d1
  umount -lf /data/d1
  fuser -ck /data/d2
  umount -lf /data/d2
  fuser -ck /data/d3
  umount -lf /data/d3
  ```

#### 关机前手动卸载磁盘阵列

利用systemd服务实现关机前自动卸载磁盘阵列常常导致无法正常关机，因此使用以下手动操作流程。

```bash
# 将数据写回磁盘
[root~] sync; sync; sync
# 杀死正在占用磁盘阵列的进程
[root~] bumountRAID
# 手动卸载磁盘阵列
[root~] umountRAID
# 关机
[root~] shutdown now
```

#### fuser使用说明

```bash
# fuser命令确认有那些进程在占用该目录：发现是pid为1757的mysql用户起的进程在占用该目录
[root@localhost /]# fuser -cu /dev/sdb1
/dev/sdb1:                1757c(mysql)

# 直接使用fuser的k参数进行kill：若发现占用进程并杀死，则返回0；若未发现占用进程或未杀死，则返回1
[root@localhost /]# fuser -ck /dev/sdb1
/data1/img:                1757c
```

## SSH 服务安全设定

sshd 的安全是指它在 Internet 上传递的数据是加密的，但 sshd 服务本身并不那样安全。sshd 安全设定从以下几个方面来进行：
* 强化服务器软件本身的设定：/etc/ssh/sshd_config
  
  * 禁止 root 和 nossh 群组用户使用 sshd 的服务；
  
* 启动 ssh 服务在非正规端口，而非默认端口 22：很多 cracker 会使用扫描程序乱扫整个 Internet 的埠口漏洞，port 22 就是一个常被扫描的端口

  * 修改ssh配置文件

    ```
    [root@ ~]$ vi /etc/ssh/sshd_config
        # Port 22
        Port 2727
    [root@ ~]$ systemctl restart sshd.service
    ```

  * SELinux设置

    ```
    # 查看 SELinux 允许 ssh 所使用的端口
    [root@ ~]$ semanage port -l | grep ssh 
    ssh_port_t     tcp     22
    # 从 SELinux 中删除 22 端口 (会报错)
    [root@ ~]$ semanage port -d -t ssh_port_t -p tcp 22
    ValueError: Port tcp/22 is defined in policy, cannot be deleted
    # 从 SELinux 中添加 2727 端口
    [root@ ~]$ semanage port -m -t ssh_port_t -p tcp 2727
    [root@ ~]$ semanage port -l | grep ssh 
    ssh_port_t     tcp     22  2727
    ```

  * 防火墙设置

    ```
    [root@ ~]$ firewall-cmd --permanent --zone=public –remove-port=22/tcp
    [root@ ~]$ firewall-cmd --permanent --zone=public –add-port=2727/tcp
    [root@ ~]$ firewall-cmd --reload
    ```



<!-- Setup64.md ends here -->
