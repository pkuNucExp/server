<!-- opencv.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 日 10月 11 19:56:03 2020 (+0800)
;; Last-Updated: 日 10月 11 20:00:38 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 1
;; URL: http://wuhongyi.cn -->

# opencv

当前服务器安装 4.4.0 版本

说明书 https://docs.opencv.org/4.4.0/index.html

## 加载

加载 opencv

```bash
module load opencv/4.4.0
```

## 编译

编译的时候链接以下动态链接库

```bash
-std=c++11  -lopencv_calib3d -lopencv_core -lopencv_dnn -lopencv_features2d -lopencv_flann -lopencv_gapi -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_stitching -lopencv_video -lopencv_videoio
```

示例，将 *main.cc* 编译成可执行文件 *123*

```bash
g++ -std=c++11 main.cc -lopencv_calib3d -lopencv_core -lopencv_dnn -lopencv_features2d -lopencv_flann -lopencv_gapi -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_stitching -lopencv_video -lopencv_videoio -o 123
```

包含 ROOT 

```bash
g++ -std=c++11 main.cc  `root-config --cflags --glibs` -lopencv_calib3d -lopencv_core -lopencv_dnn -lopencv_features2d -lopencv_flann -lopencv_gapi -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_stitching -lopencv_video -lopencv_videoio -o 123
```



<!-- opencv.md ends here -->
