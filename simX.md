<!-- simX.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 六 8月 15 15:06:03 2020 (+0800)
;; Last-Updated: 六 8月 15 15:10:26 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 1
;; URL: http://wuhongyi.cn -->

# simX

## 64 服务器

.bashrc 中添加以下配置

```bash
export AUSALIB_INC_DIR=/opt/ausalib/include
export AUSALIB_LIB_DIR=/opt/ausalib

export SIMX_INC_DIR=/opt/simX/include
export SIMX_LIB_DIR=/opt/simX
```

该程序依赖于 root 软件，当前程序基于 root 6.12.06 编译，请确保使用该版本。

```bash
module load root/6.12.06
```

可执行程序

```bash
/opt/simX/simX
```

运行的一些相关输入脚本，可参考

```txt
/opt/simX/runner
```




<!-- simX.md ends here -->
