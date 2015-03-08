---
layout: post
title: 我的金融工程工具箱
categories: quant
excerpt: <p>说是金融工程工具箱，其实只涉及到程序化交易的相关工具。这也是我学习程序化交易的一点阶段总结。</p>
---

说是金融工程工具箱，其实只涉及到程序化交易的相关工具（我要当一枚P quant :grimacing:）。下面分几类列一下我的用过的工具，这篇日志会持续更新。

## Paper Trading

这里的paper trading是指纯手动的模拟交易。为什么把paper trading工具摆在第一位，因为股票交易做为一种技能，在进入实盘之前进行大量的练习十分有益；而对于金融工程或者经济研究者，也能通过观察数据，和动手实践来获得灵感。对我来说模拟交易也是一个很好玩的游戏，经常没事就打开来刷刷。我常用的paper trading工具有：

* [ChartIQ](https://itunes.apple.com/cn/app/chartiq-practice-trading-simulator/id517702104?l=en&mt=8)：功能丰富，可惜只支持US的股票
* 国内的部分看盘软件如[同花顺](http://10jkqa.com.cn)也有提供类似功能，但是功能没有ChartIQ丰富。而且会显示日期股票名称，对A股熟悉的人基本会知道后面的行情。。。

## 数据源

我暂时只用到A股的日线历史数据，收费的没用过，免费的用过Yahoo和雪球的API。Yahoo的优点是历史悠久很多相关的library，缺点是数据质量不是很好。雪球跟yahoo相反，数据完整但是调用起来不够方便。

当下的财务数据也可以通过雪球的json api获取，但是暂时没有发现能不能调用历史数据。

雪球的日线数据可以这样调用：

{% highlight python %}
from StringIO import StringIO
import pandas as pd
import requests

def download(stock):
    link = "http://xueqiu.com/S/%s/historical.csv" % stock
    header = {
        "User-Agent" : 
        "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.111 Safari/537.36"
    } # 不加http header会禁止访问
    
    r = requests.get(link, headers=header)
    
    res = pd.DataFrame.from_csv(StringIO(r.content), index_col=1, parse_dates=True)
    return res
{% endhighlight %}

然后```sh000001 = download('sh000001')```就可以了。



## 开发环境

程序化和高频交易流行之后，出现了很多开源的程序化交易工具，其中编程语言使用率最多的要数python和R了。我个人主要用的是python，所以以下只介绍python相关的库。

* 基本
    * [IPython](http://ipython.org/)：python命令行，notebook模式太好用了
    * [pandas](pandas.pydata.org)：数据分析标配，华尔街大佬做的
    * [matplotlib](matplotlib.org)/[mpld3](https://mpld3.github.io)/[bokeh](bokeh.pydata.org)： 数据可视化
* 回测
    * [zipline](https://github.com/quantopian/zipline)：Quantopian使用的回测程序
    * [prophet](http://prophet.michaelsu.io)：简单易学的api，还在beta阶段
    * [pyalgotrade](https://github.com/gbeced/pyalgotrade)： 事件驱动，我还没有用过，以后会试试
    * PS: 个人更加喜欢像prophet这样的microframework，使用起来非常直观，限制更少而且代码重用性也很高。
* 数学模型
    * 参见[这里](https://github.com/vinta/awesome-python#science-and-data-analysis)
* 技术分析
    * [TA-Lib](https://github.com/mrjbq7/ta-lib)：调用C++写的ta-lib，指标很全

---

暂时想到这么多，以后继续添加。




