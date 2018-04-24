---
title: 如何发布带图片的博客
date: 2018-04-24 15:49:58
categories: hexo
tags: hexo

---

# 带图片的博客

## 第一步

修改hexo博客项目根目录_config.yml配置文件post_asset_folder项为true。

## 第二步

hexo new “hexo发布带图片博客”

## 第三步

在source/_post文件夹里面就会出现一个“hexo发布带图片博客.md”的文件和一个“hexo发布带图片博客”的文件夹。



## 第四步

引用图片如下： （这里不能显示代码，所以贴图了）
{% asset_img example1.jpg  %}

比如我下面这张图叫Sheild.jpg,我引用的方式就是

{% asset_img example2.jpg  %}

效果图如下：

{% asset_img sheild.jpg sheild! %}