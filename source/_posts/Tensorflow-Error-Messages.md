---
title: Tensorflow Error Messages
date: 2021-01-03 10:39:52
tags:
- Python
- Machine Learn
categories:
- [Machine Learn,Tensorflow]
---

1.

Error

```
ValueError: ('Error when checking model target: expected no data, but got:', array(['6947', '7232', '7967', ..., '5646', '3554', '4656'], dtype='<U4'))
```

Reason

```
When using model.fit() the training data is not matching to the label array
In other words, the length of training data array should be the same as label array
```



2.

Error

```
ValueError: Please provide as model inputs either a single array or a list of arrays.
```

Solution

```
training_data=np.array(training_ataset)
```



