---
title: python
date: 2022-01-07 15:47:24
tags:
categories:
---



# python 降级

打开anaconda prompt

然后输入指令

```bash
conda install python=3.6
```



anaconda 是包管理工具

python降级时，还会帮我们做环境适配



# pip

```bash
pip uninstall Pillow
```

```bash
pip install Pillow==8.1.1
```

```bash
pip install -r requirements.txt
```

```bash
-r, --requirement
# Install from the given requirements file. This option can be used multiple times.
```

不知道怎么用命令行参数的时候

直接去[官方文档](https://pip.pypa.io/en/stable/cli/pip_install/)

那里肯定有的



## python环境继承全局

pip会影响全局吗



## pypi

The Python Package Index 



# 数据处理

## DataFrame



### 选择

```python
df.loc[1]
```

![image-20220109150630032](https://gitee.com/simple_one1/pic/raw/master/image-20220109150630032.png)



```python
res['Facenet_cosine']
```

![image-20220109150809565](https://gitee.com/simple_one1/pic/raw/master/image-20220109150809565.png)



```python
len(similar_rates[similar_rates<2][similar_rates>0])
```

![image-20220109151433500](https://gitee.com/simple_one1/pic/raw/master/image-20220109151433500.png)







