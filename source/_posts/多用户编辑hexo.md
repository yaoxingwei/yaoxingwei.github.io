title: 多用户编辑hexo
author: yaoxingwei
date: 2019-07-12 00:33:29
tags:
---
### 1. 本地上传
    git init
    git add XXX //添加本地文件到仓库        
    git commit -m "blog源文件" //添加commit
    git branch hexo //添加本地仓库分支hexo
    git remote add origin <server>	// 添加远程仓库
    git push origin hexo //将本地仓库的源文件推送到远程仓库hexo分支
> Note1: 不建议将配置文件传上去:
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
_config.yml

> Note2: 需要删除themes下面的 .git 文件夹。不然会冲突导致上传失败。

### 其他用户操作
    git clone <server> hexo //<server> 是指在线仓库的地址
    cd hexo 
    npm install
    
### 同步操作
    git pull origin hexo  //先pull完成本地与远端的融合
    hexo new post " new blog name"
    git add source
    git commit -m "XX"
    git push origin hexo
    hexo d -g  // TODO: need test