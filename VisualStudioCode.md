<!-- VisualStudioCode.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 四 12月 31 16:17:12 2020 (+0800)
;; Last-Updated: 四 12月 31 16:29:25 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 3
;; URL: http://wuhongyi.cn -->

# Visual Studio Code

## 软件启动

使用 Visual Studio Code 只需要在终端中输入以下命令

```bash
code
```

**请根据个人使用习惯进行配置以及安装扩展插件。**


## 插件安装

- [VScode插件推荐（全面）](https://www.jianshu.com/p/3eebde5748a6)
- [VsCode通过SSH连接远程服务器开发](https://www.cnblogs.com/chnmig/p/12160248.html)



## CENTOS 安装

官方说明 https://code.visualstudio.com/docs


```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'


yum check-update
sudo yum install code
```


<!-- VisualStudioCode.md ends here -->
