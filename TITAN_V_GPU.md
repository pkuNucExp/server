# GPU 安装记录

2020.09.15，我们在64服务器上安装了一块显卡(Nivida TITAN V).

## driver/cuda

显卡的驱动和CUDA是两个不同的组件。驱动用于系统了解如何与硬件进行通信，CUDA则是用于进行GPU编程的编译器、函数库、调试器等组成的开发环境。

服务器上的显卡驱动和CUDA是分别安装的，步骤如下。


## 最后一次成功安装的步骤

+ module load gcc/9.3.0
+ sh NVIDIA-Linux-x86_64-450.51.05.run
+ sh cuda_11.0.3_450.51.06_linux.run

第一步是加载gcc 9.3.0，第二部安装驱动，第三步安装cuda。

NVIDIA-Linux-x86_64-450.51.05.run文件包含了显卡的驱动，是工程师从nvidia官网下载好后拷贝过来的。

cuda_11.0.3_450.51.06_linux.run文件包含了显卡驱动和cuda开发环境，是从[nvidia的cuda页面](https://developer.nvidia.com/cuda-downloads)下载到的。

其中，安装驱动步骤会提示gcc版本和编译内核时使用的gcc版本不同，直接选择忽略检查即可，其余可用默认选项。

第三步安装cuda时去掉driver一项（因为前面一步已经安装过了）。同时在option中去掉了为每一位用户创建快捷方式的选项。

上述.run文件均可在`/data/d1/gj/nvdriver`目录下找到。

## 失败案例

官网提供的CUDA有几种安装方法，不算网络安装的话，针对centos 7提供了.run和.rpm两种安装包。

.rpm多少算是centos下安装程序的标准做法，.run则稍微有点野，anyway，都是官方支持的安装方式。

最初，工程师安装了驱动（上面的第二步的.run文件（也加载了gcc 9.3.0））.经测试，系统可以识别到显卡。

之后从nvidia下载了rpm的cuda包，按照说明安装（rpm -i xxx.run; yum install xxx）后系统无法驱动显卡。推测是两个驱动争风吃醋导致显卡不工作的。

通过yum卸载掉一切与nvidia、cuda有关的包之后，重新安装NVIDIA-Linux-x86_64-450.51.05.run，系统可以识别到显卡。但由于cuda已卸载，无法使用cuda。

此外，如果使用系统默认的gcc（gcc4.9.2）时，NVIDIA-Linux-x86_64-450.51.05.run无法安装，错误提示表明编译内核出错。

如果使用NVIDIA-Linux-x86_64-450.51.05.run卸载驱动，再通过rpm安装cuda和驱动，依然会失败。


推测使用默认gcc4.9.2时通过.run文件安装驱动会失败的可能的原因：

1. 可能是系统原带的gcc是4.8.5，而4.9.2和4.8.5某些行为不一致，但在9.3.0中又修复了。
2. cuda的文档中提到cuda需要c++11特性，因此需要gcc>5。虽说这一步是按照驱动而不是cuda，但是依然有可能驱动中用到了c++11特性。

## cuda安装位置

全部安装完成后，cuda被安装在/usr/local/cuda处。（/usr/local/cuda是一个符号链接，链接到/usr/local/cuda-11.0）。

使用时需要添加环境变量。相应的modulefile已经添加好了，可以直接

```
module load cuda/11.0.3
```

来载入cuda模块。

## 允许非root用户对CUDA程序进行分析

2020.09.20

在/etc/modprobe.d/下新建了一个文件nsight-compute-profile.conf

内容是options nvidia "NVreg_RestrictProfilingToAdminUsers=0"

该设置在每次系统启动时会影响显卡驱动，使得非root用户可以使用Nsight Compute等工具对CUDA程序运行状况进行分析。

详细情况可参考 [https://developer.nvidia.com/nvidia-development-tools-solutions-ERR_NVGPUCTRPERM-permission-issue-performance-counters](https://developer.nvidia.com/nvidia-development-tools-solutions-ERR_NVGPUCTRPERM-permission-issue-performance-counters)

