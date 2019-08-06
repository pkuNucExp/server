<!-- Setup64.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 二 8月  6 17:10:20 2019 (+0800)
;; Last-Updated: 二 8月  6 18:26:38 2019 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 9
;; URL: http://wuhongyi.cn -->

# 64服务器管理员配置


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


#python3
yum install python36.x86_64 python36-devel.x86_64 python36-libs.x86_64 python36-tkinter.x86_64 python36-pip.noarch python36-cffi.x86_64 python36-cryptography.x86_64 python36-cryptography-vectors.noarch python36-decorator.noarch python36-idna.noarch python36-ipython_genutils.noarch python36-ply.noarch python36-pyasn1.noarch python36-pycparser.noarch python36-six.noarch python36-traitlets.noarch python36-mysql.x86_64 python36-jinja2.noarch


#clang编译器
yum install clang.x86_64 clang-devel.x86_64

# ROOT
yum install lz4-devel.x86_64 ruby-devel.x86_64 expect-devel.x86_64  glew.x86_64 gsl-devel.x86_64 libxml2-static.x86_64 R.x86_64 R-RInside.x86_64 R-RInside-devel.x86_64 R-Rcpp.x86_64 R-Rcpp-devel.x86_64 cfitsio.x86_64 cfitsio-devel.x86_64 davix.x86_64 davix-devel.x86_64 ftgl.x86_64 ftgl-devel.x86_64 gfal2.x86_64 gfal2-all.x86_64 gfal2-devel.x86_64 mysql++.x86_64 mysql++-devel.x86_64 pythia8.x86_64 pythia8-devel.x86_64 unuran.x86_64 unuran-devel.x86_64 xrootd.x86_64 xrootd-client.x86_64 xrootd-client-devel.x86_64 xrootd-devel.x86_64
```

  



<!-- Setup64.md ends here -->
