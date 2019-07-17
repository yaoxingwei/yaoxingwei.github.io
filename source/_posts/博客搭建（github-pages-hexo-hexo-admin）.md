title: 博客搭建（github pages + hexo + hexo-admin）
author: yaoxingwei
tags: []
categories: []
date: 2019-07-10 16:20:00
---
### 1. github pages + hexo配置
	1. 参考：https://www.cnblogs.com/jackyroc/p/7681938.html
    2. 注意github pages的setting，repo name 一定是 xxx.github.io的格式
   ![upload successful](/images/pasted-0.png)
    
###	2. hexo编辑器

	1. 找了很多，发现个hexo原生的hexo-admin，方便快捷。配置参考：
    https://blog.csdn.net/light_fisher/article/details/85145204
	2. 后续会用更复杂的编译器吧......
    
### 3. markdown语法
[参考文章：(https://www.jianshu.com/p/335db5716248)](https://www.jianshu.com/p/335db5716248)
###### 标题
    #
    ##
    ...
    #####
###### 高亮
	>
###### 插入链接或图片
	[点击跳转至百度](http://www.baidu.com)
	![图片](https://upload-images.jianshu.io/upload_images/703764-605e3cc2ecb664f6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 注：引用图片和链接的唯一区别就是在最前方添加一个感叹号。

###### 列表
    * 黄瓜
    * 玉米
    * 茄子
    
    + 黄瓜
    + 玉米
    + 茄子
    
    - 黄瓜
    - 玉米
    - 茄子
    
    1. 黄瓜
    2. 玉米
    3. 茄子
    
> 注：如果在单一列表项中包含了多个段落，为了保证渲染正常，*与段落首字母之间必须保留四个空格

> 如果在列表中加入了区块引用，区域引用标记符也需要缩进4个空格

###### 分割线
    ***
    ---

###### 强调
    *这里是斜体*
    _这里是斜体_

    **这里是加粗**
    __这里是加粗__

###### 插入代码
    用反引号``包裹单行，多反引号包裹多行，如下:
    \`\`\`c/phthon/ruby/phy
    code
    \`\`\`
```c
#include <stdio.h>

int main()
{
    /* 我的第一个 C 程序 */
    printf("Hello, World! \n");

    return 0;
}
```

###### 插入表格
    表头|条目一|条目二
    :---:|:---:|:---:
    项目|项目一|项目二
###### 特殊符号
    Markdown使用反斜杠\插入语法中用到的特殊符号。在Markdown中，主要有以下几种特殊符号需要处理：
    \   反斜线
    `   反引号
    *   星号
    _   底线
    {}  花括号
    []  方括号
    ()  括弧
    #   井字号
    +   加号
    -   减号
    .   英文句点
    !   惊叹号
###### 文字上色
    1. 先用Markdown编辑完成
    2. 导出为html，在需要上色的部分手动添加标签<font color='#ff0000'></font>保存即可。
###### 换行：
    <br>

###### 段首缩进：
    &ensp; or &#8194; 表示一个半角的空格
    &emsp; or &#8195;  表示一个全角的空格
    &emsp;&emsp; 两个全角的空格（用的比较多）
    &nbsp; or &#160; 不断行的空白格