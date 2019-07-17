title: 多用户编辑hexo
author: yaoxingwei
date: 2019-07-12 00:33:29
tags:
---
### 其他用户操作
    git clone -b hexo git@github.com:yourname/yourname.github.io.git  //将Github中hexo分支clone到本地
    cd  yourname.github.io  //切换到刚刚clone的文件夹内
    npm install    //注意，这里一定要切换到刚刚clone的文件夹内执行，安装必要的所需组件，不用init
    hexo new post "new blog name"   //新建一个.md文件，并编辑完成自己的博客内容
    git add source  //经测试每次只要更新sorcerer中的文件到Github中即可，因为只是新建了一篇新博客
    git commit -m "XX"
    git push origin hexo  //更新分支
    hexo d -g   // !!!!!!!!!!!!!!这个操作有风险。。需要再研究。
    
### 同步操作
    git pull origin hexo  //先pull完成本地与远端的融合
    hexo new post " new blog name"
    git add source
    git commit -m "XX"
    git push origin hexo
    hexo d -g