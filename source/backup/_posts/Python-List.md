---
title: Python List
date: 2021-01-02 23:12:21
tags:
- Python
- Tutorial
categories:
- [Python,Tutorial]
---

1.Don't forget the comma

```python
		[
            ['j1','m1','x1','s1','k','s2','x2','m2','j2'],
            ['', '', '', '', '', '', '', '', ''],
            ['','p1','','','','','','p2',''],
            ['b1','','b2','','b3','','b4','','b5'],
            ['', '', '', '', '', '', '', '', ''],
            ['', '', '', '', '', '', '', '', ''],
            ['B1', '', 'B2', '', 'B3', '', 'B4', '', 'B5'],
            ['', 'P1', '', '', '', '', '', 'P2', ''],
            ['', '', '', '', '', '', '', '', ''],
            ['J1','M1','X1','S1','K','S2','X2','M2','J2']
        ]
```

---

2.delete element

```python
a=[1,2,3]
del(a[2]) # arg is address
print(a)

output:
[1,2]
```

---

3.Deep copy

When you put a Object in a List

You actually store a address in List

So it's easily to make a mistake

You think you put different object in the List

But actually, you just put an address in List for many time

And all address in a List point to the same memory

The solution is use deep copy

And new a Object every time, not just use setter or assign

Remember:

```
Setter will not create a new object
Assignment will not create a new object 
(assignment just change the variable's address to the target)
```

Wrong Example

```python
nextState = State(self.player, self.agent)
nextState.board = current_state.board 
# will not create a new board, just point to the same memory
```

Right Example

```python
import copy

nextState = State(self.player, self.agent) # create a new object
nextState.board = copy.deepcopy(current_state.board) 
# create it's own board instead of point to the same memory
```

---

4.   2 dimension array

```python
matrix = []
 for i in range(3):
      matrix.append([0] * 3)
```

Or

```python 
n = 3
m = 3
dp = [[0 for i in range(n)] for j in range(m)]
```







