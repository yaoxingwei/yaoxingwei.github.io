title: 内存泄漏debug - Valgrind/mtrace 在ARM平台使用
author: yaoxingwei
date: 2019-08-21 17:14:58
tags:
---
# Valgrind usage
#### 下载valgrind源码
[源码地址](http://www.valgrind.org/downloads/)

#### 交叉编译

    ./autogen.sh
    ./configure --host=arm-linux-gnueabihf --prefix=/xxx/valgrind-3.15.0/out/ CC=arm-linux-gnueabihf-gcc
    make
    make install

#### copy可执行文件到arm平台
    scp out/bin/valgrind xxx.xxx.xxx.xxx:/home/xxx
    scp out/lib/valgrind/memcheck-arm-linux xxx.xxx.xxx.xxx:/home/xxx/lib
    
> note: 本文只使用memcheck工具，如果需要其他工具，需要copy相应的lib库的文件到arm平台

#### 配置运行环境
    export VALGRIND_LIB=/home/xxx/lib

#### 运行valgrind
    ./valgrind --leak-check=full --log-file=/home/xxx/log ./xxx(Linux program)
    
> note: valgrind需要libc支持debug info。如果当前文件系统libc不支持。可以copy交叉工具链的带debug info的libc到当前arm平台。然后设置LD_LIBRARY_PATH。


# mtrace usage
代码格式：

    #include <mcheck.h>
    void mtrace(void);
    // trace code ...
    // ...
    // ...
    void muntrace(void);
 
设置输出log地址：
 
     $ export MALLOC_TRACE=/home/xxx/xxx/trace.log

输入log格式转换：

    mtrace xxx<program> trace.log > trace_trans.log
    
# 内存泄漏tips

1. 使用valgrind可以比较方便查看内存使用情况
2. mtrace输出的memory地址，结合出错memory地址，可以发现是否是内存越界。如果是，多检查字符串操作。
3. alloc/free函数重新封装，可以通过code打印memory使用情况，类似mtrace。