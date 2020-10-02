<!-- GRAZING.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 五 10月  2 19:02:35 2020 (+0800)
;; Last-Updated: 五 10月  2 19:23:15 2020 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 3
;; URL: http://wuhongyi.cn -->

# GRAZING

**A Fortran program for estimating reactions in collision between Heavy Nuclei**

http://personalpages.to.infn.it/~nanni/grazing/


在个人 *.bashrc* 配置文件中添加以下配置

```bash
export GRAZING_DIR=/opt/GRAZING/data
export PATH=$PATH:/opt/GRAZING
```


运行方式(终端中输入以下命令，然后按回车，根据提示进行参数输入)

```bash
grazing_9_64bit
```

## 参考示例

calculate a fusion excitation function

```
OK
   28   58   28   60      ! Z_a,A_a,Z_A,A_A 
s       !  cannot be changed                                  
     !except if you change to a and enter accuracy here     
no      !additional output, special options, don`t change      
   1   !inelastic options                                       
  94.00000      ! Center of mass energy                               
   1      ! leg,  cannot be changed                             
   2.0000 120.0000      ! Step in E_cm and maximum(or minimum)                
600.00      ! Allowed time in min. Delete line if Step is 0.      
cm    ! lab=lab, cm=center of mass, both=both system            
   0.000   0.000     ! energy resolution and cutt-off   
no     ! variable for printout             
no       ! new run enters at Z_a,A_aetc    
```







<!-- GRAZING.md ends here -->
