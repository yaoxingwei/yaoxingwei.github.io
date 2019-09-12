title: Linux开发 - debug线程cpu占用过高
author: yaoxingwei
date: 2019-07-19 12:18:34
tags:
---
### 1. 重编译功能完全的ps命令(optional)
>  [源码地址](https://gitlab.com/procps-ng/procps)
			
###### 编译脚本   


```c
#!/bin/sh

CROSS_COMPILE=arm-linux-gnueabihf-
HOST=arm-linux-gnueabihf
TARGET_DIR=$(cd `dirname $0`; pwd)/out

build_procps() {
    ac_cv_func_realloc_0_nonnull=yes \
    ac_cv_func_malloc_0_nonnull=yes \
    ./configure --host=$HOST --prefix=$TARGET_DIR --enable-static --without-ncurses
    make ; make install || exit 1
}

./autogen.sh  # maybe need to install libtool-bin
build_procps
```

### 2. 利用ps命令查看线程占用情况

    ps H -eo user,pid,ppid,tid,time,%cpu,cmd --sort=%cpu
    
>  该命令可以查看各进程&线程占用cpu情况并排序显示。


### 3. 根据线程id查找代码对应thread

  ![upload successful](/images/pasted-2.png)


在相应的线程代码里加打印，输出线程tid。
````c
#include <sys/syscall.h>
printf("%s tid:%lu pid:%u\n", __func__, syscall(SYS_gettid), (unsigned int)pthread_self())

````

### 总结：多数占用高是线程pooling导致。可考虑阻塞方式。