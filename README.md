<!-- README.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 六 6月 29 21:56:56 2019 (+0800)
;; Last-Updated: 五 7月  5 18:23:21 2019 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 16
;; URL: http://wuhongyi.cn -->

# README

```
module avail 显示可以使用的模块 
module load 加载模块 
module unload 卸载模块 
module list 显示已经加载的模块
```

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
	- 6.12.06 (no) 依赖gcc4.9.4,cmake3.7.2,python2.7.16,python3.6.9
	- 6.16.00 (no)
- geant4
	- 4.9.6
	- 4.10.01
	- 4.10.02
	- 4.10.03
	- 4.10.04
	- 4.10.05

软件依赖
- root 5.34.38
	- gcc 4.9.4	
- root 6.12.06
	- gcc 4.9.4	
	- cmake 3.7
- root 6.16.00
	- gcc 4.9.4	
	
	
<!-- README.md ends here -->
