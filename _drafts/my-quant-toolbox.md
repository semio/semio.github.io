---
layout: post
title: 我的金融工程工具箱
categories: quant
excerpt: 总结一下我用过的金融市场相关的工具
---

说是金融工程工具箱，其实只涉及到程序化交易的相关工具（我要当一枚P quant :grimacing:）。下面分几类列一下我的工具箱，这篇日志会持续更新。

## Paper Trading

为什么把paper trading工具摆在第一位，因为股票交易做为一种技能，很自然需要大量的练习；而对于金融工程或者经济研究者，也能通过观察数据，和动手实践来获得灵感。我常用的paper trading工具有：

1. [ChartIQ](https://itunes.apple.com/cn/app/chartiq-practice-trading-simulator/id517702104?l=en&mt=8)：功能丰富，可惜只支持US的股票
2. 国内的部分看盘软件如[同花顺](http://10jkqa.com.cn)也有提供类似功能，但是功能没有ChartIQ丰富

## 数据源

我暂时只用到A股的日线历史数据，收费的没用过，免费的用过Yahoo和雪球的API。Yahoo的优点是历史悠久很多相关的library，缺点是数据质量不是很好。雪球跟yahoo相反，数据完整但是调用起来不够方便。雪球的数据可以这样调用：

```python
from StringIO import StringIO
import pandas as pd
import requests

def download(stock):
    xueqiu_l1 = "http://xueqiu.com/S/"
    xueqiu_l2 = "/historical.csv"
    link = xueqiu_l1 + stock + xueqiu_l2
    header = {
        "User-Agent" : 
        "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.111 Safari/537.36"
    } # 雪球前段时间遭到攻击，对http请求进行了过滤，加上user agent绕过。
    
    r = requests.get(link, headers=header)
    
    res = pd.DataFrame.from_csv(StringIO(r.content), index_col=1, parse_dates=True)
    return res
```

然后```sh000001 = download('sh000001')```就可以了。

## 回测 

程序化和高频交易在华尔街流行之后，出现了很多开源的程序化交易工具，其中最多的编程语言有python和R。我个人主要用的是python（另外也很关注最近新出的[Julia](http://julialang.org/)语言），所以以下只介绍python相关的库：

* [zipline](https://github.com/quantopian/zipline)：Quantopian使用的回测程序
* [prophet](http://prophet.michaelsu.io)：简单易学的api，还在beta阶段
* [pyalgotrade](https://github.com/gbeced/pyalgotrade)： 事件驱动，我还没有用过，以后会试试

个人更加喜欢像prophet这样的microframework，使用起来非常直观，限制更少而且代码重用性也很高。


