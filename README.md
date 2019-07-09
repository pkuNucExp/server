<!-- README.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 六 6月 29 21:56:56 2019 (+0800)
;; Last-Updated: 二 7月  9 13:17:35 2019 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 23
;; URL: http://wuhongyi.cn -->

# README

**root6尚未安装**

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

你将会看到如下

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

例如你想使用 geant4.10.04p03，则输入以下命令即可加载所需的环境

```bash
module load gcc/4.9.4
module load cmake/3.7.2
module load geant4/4.10.04p03
```




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
	- 6.12.06 (no) 依赖gcc4.9.4,cmake3.7.2,python3.6.9
	- 6.16.00 (no)
- geant4
	- 4.9.6p04   (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.00p04 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.01p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.02p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.03p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.04p03 (ok) 依赖gcc4.9.4,cmake3.7.2
	- 4.10.05p01 (ok) 依赖gcc4.9.4,cmake3.7.2


	
	
<!-- README.md ends here -->
