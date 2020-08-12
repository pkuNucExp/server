<!-- README.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 六 6月 29 21:56:56 2019 (+0800)
;; Last-Updated: 三 8月 12 14:10:25 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 35
;; URL: http://wuhongyi.cn -->

# README

- 如果需要其它软件/版本，请联系管理员安装。
- 安装多版本及多版本的任意切换，目的在于对软件进行测试。ROOT/GEANT4属于发展中的软件，还有很多问题，当你发现程序存在问题一直无法解决时，可以更换其它版本测试是否是该版本存在问题。


Environment modules 提供了一种设置shell环境（PATH, MANPATH, INCLUDE, LD\_LIBRARY\_PATH）的方法，通过使用module命令，来设置和取消你的路径和环境变量。

记住以下常用命令

```bash
module avail   #显示可以使用的模块 
module load    #加载模块 
module unload  #卸载模块 
module list    #显示已经加载的模块
```

## 加载配置

在命令行中执行以下命令查看当前可加载的软件

```bash
module avail
```

以 **服务器30** 为例，你将会看到如下

```
------------------------ /usr/share/Modules/modulefiles ------------------------
dot         module-git  module-info modules     null        use.own

------------------------------- /etc/modulefiles -------------------------------
cmake/3.14.5      geant4/4.10.01p03 geant4/4.9.6p04   root/6.12.06
cmake/3.7.2       geant4/4.10.02p03 mpich-x86_64      root/6.16.00
gcc/4.9.4         geant4/4.10.03p03 python/2.7.16
gcc/7.3.0         geant4/4.10.04p03 python/3.6.9
geant4/4.10.00p04 geant4/4.10.05p01 root/5.34.38
```

例如你想使用 root5.34.38，则输入以下命令即可加载所需的环境

```bash
module load root/5.34.38
```


**服务器 30 与 服务器 64 由于系统版本不同，30 系统自身软件版本较低，因此在使用 30 服务器时，需要加载的配置多一些。每个人根据使用的服务器查看以下对应的说明即可。**


例如你想使用 geant4.10.04p03，则 **服务器30** 输入以下命令即可加载所需的环境

```bash
module load gcc/4.9.4
module load cmake/3.7.2
module load geant4/4.10.04p03
```

在 **服务器64** 则只需要输入以下命令即可 

```bash
module load geant4/4.10.04p03
```

当然，每次打开终端都要这样配置也没有必要，可将常用软件版本配置添加在 **.bashrc** 文件中。如何配置请看以下对应服务器的说明。


## 服务器 30

安装多版本的软件有
- gcc
	- 4.4.7 系统默认
	- 4.9.4 (ok)
	- 7.3.0 (ok)
- cmake
	- 2.8.12.2  系统默认
	- 3.7.2 (ok)
	- 3.14.5 (ok) 依赖gcc4.9.4
- python
	- 2.6.6 系统默认
	- 2.7.16 (ok)
	- 3.6.9 (ok)
- root
	- 5.34.38 (ok)
	- 6.12.06 (ok) 依赖gcc4.9.4,cmake3.7.2,python3.6.9
	- 6.16.00 (no) 依赖gcc4.9.4,cmake3.7.2,python3.6.9
- geant4
	- 4.9.6p04   (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.00p04 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.01p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.02p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.03p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.04p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.05p01 (ok) 依赖gcc4.9.4,cmake3.7.2

**软件后面注释的软件依赖，意味着你要使用该软件，则需要加载相对应的依赖软件。**


懒人模式，快速配置 ROOT/GEANT4，在 *.bashrc* 添加以下配置即可

```bash
## 根据需要选择想要的版本

module load root/5.34.38

module load gcc/4.9.4
module load cmake/3.7.2
module load geant4/4.10.04p03
```

记得删除 *.bashrc* 中之前 source 的配置。


## 服务器 64

安装多版本的软件有
- gcc
	- 4.9.2 系统默认
	- 7.3.0 (ok)
- cmake
	- 3.10.3  系统默认
- emacs	
	- 24.3.1  系统默认
- python
	- 2.7.5 系统默认(python2)
	- 3.6.8 系统默认(python3) 
- vim
	- 7.4 系统默认
	- 8.0 (ok)
- root
	- 5.34.38 (ok)
	- 6.06.08 (ok)
	- 6.12.06 (ok)
	- 6.14.06 (ok)
	- 6.16.00 (ok)
- geant4
	- 4.9.6p04   (ok) 
	- 4.10.00p04 (ok) 
	- 4.10.01p03 (ok) 
	- 4.10.02p03 (ok) 
	- 4.10.03p03 (ok) 
	- 4.10.04p03 (ok) 
	- 4.10.05p01 (ok) 


懒人模式，快速配置 ROOT/GEANT4，在 *.bashrc* 添加以下配置即可

```bash
## 根据需要选择想要的版本

module load root/5.34.38

module load geant4/4.10.04p03
```

记得删除 *.bashrc* 中之前 source 的配置。

下图为吴鸿毅在服务器64上的个人配置

![bashrc](img/wuhongyi64bashrc.png)

## 关于网络

30/64 服务器为数据处理服务器，为了安全，没有直接连上公网，当前通过我们的28网络服务器来作为中转。

如果你需要访问外网下载或者上传数据，则在 *.bashrc* 添加以下配置即可

```bash
#添加Proxy代理信息
export http_proxy=http://162.105.151.28:3128/
export https_proxy=http://162.105.151.28:3128/
```

## 关于如何配置多版本

如果你对如何实现软件多版本配置感兴趣，可查看 **/etc/modulefiles** 目录下的配置，以及 Baidu/Google 关键词 **Environment Modules**。




	
<!-- README.md ends here -->
