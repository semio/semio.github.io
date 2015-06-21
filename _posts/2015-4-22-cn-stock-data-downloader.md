---
title: 股票数据下载器
layout: post
categories:
    - tools
    - trading
excerpt: <p>最近开始着手写一个A股的股票数据下载工具，用于获取基本面和价格等信息。</p>
---

最近在学习价值分析，学到了一些东西就想在A股市场上测试一下。无奈股票软件提供的数据有限，通常财务数据都只提供最近公布的数据，以前的数据就只能F10查看了，所以就萌生了自己写个的念头。 搜索一圈之后发现了[FQuantToolbox](1), 它提供的数据全部是用各个财经网站提供的免费信息实现的，只是这个工具是Matlab写的，我自己用不上。

还好网络爬虫和文本处理刚好是python的强项，我想要实现一个类似的工具也不难。上个周末已经实现了两个功能，项目源码放在[github](2)上。


[1]: https://mp.weixin.qq.com/s?__biz=MzA5NzEzNDk4Mw==&mid=203362468&idx=1&sn=e4de198d87377b1693a475201ac192b8&3rd=MzA3MDU4NTYzMw==&scene=6#rd
[2]: https://github.com/semio/cnstockdata
