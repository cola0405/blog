---
title: pandas
date: 2022-09-27 15:10:59
tags:
categories:
---





```python
The kind of plot to produce:

‘line’ : line plot (default)

‘bar’ : vertical bar plot

‘barh’ : horizontal bar plot

‘hist’ : histogram

‘box’ : boxplot

‘kde’ : Kernel Density Estimation plot

‘density’ : same as ‘kde’

‘area’ : area plot

‘pie’ : pie plot

‘scatter’ : scatter plot (DataFrame only)

‘hexbin’ : hexbin plot (DataFrame only)
```





## bin

统计堆







## plot

subplots 可能会导致显示出问题



## series

交换index和value

```python
c = pd.Series(c.index, c.values)
```

