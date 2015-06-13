---
layout: post
title: "Untitled"
tags:
    - python
    - notebook
---
This is a just test notebook.

## Now it is the codes

Loalalskj!


<div class="input_prompt">
In [1]:
</div>

```python
'like this'
```

<div class="output_prompt">
Out [1]:
</div>




    'like this'



<div class="input_prompt">
In [1]:
</div>

```python
import pandas as pd
import numpy as np
```

<div class="input_prompt">
In [2]:
</div>

```python
import scipy.stats as stats
```

<div class="input_prompt">
In [3]:
</div>

```python
%matplotlib inline
```

<div class="input_prompt">
In [26]:
</div>

```python
import matplotlib as mpl
import seaborn as sbn
from matplotlib.pylab import plot
```

<div class="input_prompt">
In [21]:
</div>

```python
mpl.rcParams['figure.figsize'] = (15.0, 6.0)
sbn.set_context(context='talk')
```

<div class="input_prompt">
In [23]:
</div>

```python
x = np.linspace(1, 7, 50)
y = 3 + 2*x +1.5*np.random.randn(len(x))
sbn.regplot(x, y)
```

<div class="output_prompt">
Out [23]:
</div>




    <matplotlib.axes._subplots.AxesSubplot at 0x1146cd610>




<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_7_1.png' alt='png'>


<div class="input_prompt">
In [22]:
</div>

```python
bd1 = stats.binom(20, 0.5)
k = range(40)
mpl.pylab.plot(k, bd1.pmf(k), 'o-b')
```

<div class="output_prompt">
Out [22]:
</div>




    [<matplotlib.lines.Line2D at 0x1146bc190>]




<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_8_1.png' alt='png'>


<div class="input_prompt">
In [24]:
</div>

```python
pd = stats.poisson(10)
mpl.pylab.plot(k, pd.pmf(k),'x-')
```

<div class="output_prompt">
Out [24]:
</div>




    [<matplotlib.lines.Line2D at 0x1134c4750>]




<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_9_1.png' alt='png'>


<div class="input_prompt">
In [32]:
</div>

```python
k = np.arange(30)
plot(k, pd.cdf(k))
```

<div class="output_prompt">
Out [32]:
</div>




    [<matplotlib.lines.Line2D at 0x1150f01d0>]




<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_10_1.png' alt='png'>


<div class="input_prompt">
In [37]:
</div>

```python
data = stats.norm.rvs(0, 3, size=200)
```

<div class="input_prompt">
In [40]:
</div>

```python
mpl.pyplot.hist(data)
```

<div class="output_prompt">
Out [40]:
</div>




    (array([  3.,  13.,  17.,  29.,  33.,  35.,  33.,  21.,  12.,   4.]),
     array([-7.6233984 , -6.17844032, -4.73348223, -3.28852415, -1.84356606,
            -0.39860798,  1.0463501 ,  2.49130819,  3.93626627,  5.38122436,
             6.82618244]),
     <a list of 10 Patch objects>)




<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_12_1.png' alt='png'>


<div class="input_prompt">
In [41]:
</div>

```python
pVals = pd.Series()
    # The scipy normaltest is based on D-Agostino and Pearsons test that
    # combines skew and kurtosis to produce an omnibus test of normality.
_, pVals['omnibus'] = stats.normaltest(data)
```

<div class="output_prompt">
Out [41]:
</div>


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-41-42ea9bce4218> in <module>()
    ----> 1 pVals = pd.Series()
          2     # The scipy normaltest is based on D-Agostino and Pearsons test that
          3     # combines skew and kurtosis to produce an omnibus test of normality.
          4 _, pVals['omnibus'] = stats.normaltest(data)


    AttributeError: 'rv_frozen' object has no attribute 'Series'


<div class="input_prompt">
In [42]:
</div>

```python
_ = stats.probplot(data, plot=mpl.pyplot)
```

<div class="output_prompt">
Out [42]:
</div>


<img class='img-output' src='{{ site.baseurl }}assets/images/Untitled_files/Untitled_14_0.png' alt='png'>


<div class="input_prompt">
In [None]:
</div>

```python

```
