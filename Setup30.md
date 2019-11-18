<!-- Setup30.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 二 9月  3 10:54:59 2019 (+0800)
;; Last-Updated: 一 11月 18 12:04:16 2019 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 2
;; URL: http://wuhongyi.cn -->

# README

## 关闭SELINUX

/etc/sysconfig/selinux

```bash
# This file controls the state of SELinux on the system.                        
# SELINUX= can take one of these three values:                                  
#     enforcing - SELinux security policy is enforced.                          
#     permissive - SELinux prints warnings instead of enforcing.                
#     disabled - No SELinux policy is loaded.                                   
#SELINUX=enforcing                                                              
SELINUX=disabled
# SELINUXTYPE= can take one of these two values:                                
#     targeted - Targeted processes are protected,                              
#     mls - Multi Level Security protection.                                    
SELINUXTYPE=targeted
```

<!-- Setup30.md ends here -->
