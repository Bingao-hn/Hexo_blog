---
title: hexo推送文章到github
date: 2018-04-19 19:59:09
tags: hexo

---

使git部署

npm install hexo-deployer-git --save

基本的流程到这里快要结束了

最后执行:**(**hexo clean -->hexo generate -->hexo deploy)

确认在本地上显示无误之后，就可以将 md 转为 静态网页文件，然后发布到 GitHubPages 上去了

```
hexo clean #清除缓存 网页正常情况下可以忽略此条命令
hexo g #生成静态网页
hexo d #开始部署

也可以一次性执行
hexo clean && hexo g && hexo d
```

[参考博客](https://blog.csdn.net/ainuser/article/details/77609180)

[超详细配置](https://zhuanlan.zhihu.com/p/25959864)

