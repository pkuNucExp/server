<!-- nushellx.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 一 8月 24 16:58:46 2020 (+0800)
;; Last-Updated: 一 8月 24 17:30:36 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 4
;; URL: http://wuhongyi.cn -->

# nushellx

**64 服务器上安装了 nushellx 程序**

## 配置

在个人目录下的 *.bashrc* 文件中添加以下配置

```bash
export PATH=/opt/nushellx/linux/nushellx-gfortran-bin:$PATH
export nushellx_sps=/opt/nushellx/sps/
export mass_data=/opt/nushellx/toi/mass-data/
export toi_data=/opt/nushellx/toi/toi-data/
```

## 运行

在任意位置新建一个文件夹，然后进入该文件夹

执行以下命令

```bash
shell
```

输入相应参数之后，会生成 xxx.bat 文件

然后通过以下方式运行

```bash
. xxx.bat
```


<!-- nushellx.md ends here -->
