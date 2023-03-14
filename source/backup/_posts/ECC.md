---
title: ECC
date: 2021-03-22 08:44:42
tags:
categories:
---

[Algorithm Reference](https://cryptobook.nakov.com/asymmetric-key-ciphers/elliptic-curve-cryptography-ecc)

```
Elliptic Curve Digital Signature Algorithm(ECDSA) is a cryptographic algorithm used by Bitcoin to ensure that funds can only be spent by their rightful owners.
```

```
Elliptic Curve

y^2 = (x^3 + 7) 
and ECDSA get dots scattered with Elliptic Curve

y^2 \mod p = (x^3 + 7) this is dots scattered
```

![](Snipaste_2021-03-21_18-40-09.png)

These dots are use to generate key !

> Note:
>
> mod 17 make it map to the integer from 0 to16



![](Snipaste_2021-03-21_18-41-26.png)

```
from start point to end point, need how many operations
```

```
cryptographers carefully select one of them, which generates the entire group (or subgroup) and is suitable for performance optimizations in the computations. This is the generator known as "G".
```

If a point in the curve

```
The point P {5, 8} belongs to the curve, because (5**3 + 7 - 8**2) % 17 == 0
```

EC point addition

```
Two points over an elliptic curve (EC points) can be added and the result is another point. 
```

EC point multiplication

```
If we add a point G to itself, the result is G + G = 2 * G. If we add G again to the result, we will obtain 3 * G and so on

then you will know what is "P = k * G"
(do that operation k times)
```

infinity

```
Multiplying an EC point by 0 returns a special EC point called "infinity".
```



Order, cofactor

```
Аn elliptic curve over a finite field can form a finite cyclic algebraic group, 
which consists of all the points on the curve. 
In a cyclic group, if two EC points are added or an EC point is multiplied to an integer, the result is another EC point from the same cyclic group 
(and on the same curve). 
The order of the curve is the total number of all EC points on the curve. 
```

- **h** = **n** / **r**

where

- **n** is the **order of the curve** (the number of all its points)
- **h** is the curve **cofactor** (the number of non-overlapping **subgroups** of points, which together hold all curve points)
- **r** is the **order of the subgroups** (the number of points in each subgroup, including the ***infinity*** point for each subgroup)

```
In other words, the points over an elliptic curve stay in one or several non-overlapping subsets, called cyclic subgroups. 
The number of subgroups is called "cofactor". 
The total number of points in all subgroups is called "order" of the curve 
and is usually denoted by n. 
If the curve consists of only one cyclic subgroup, its cofactor h = 1. If the curve consists of several subgroups, its cofactor > 1.
```

- Example of elliptic curve having **cofactor** = **1** is `secp256k1`.
- Example of elliptic curve having **cofactor** = **8** is `Curve25519`.
- Example of elliptic curve having **cofactor** = **4** is `Curve448`.

Generator

```
For the elliptic curves over finite fields, 
the ECC cryptosystems define a special pre-defined (constant) EC point called generator point G (base point), 
which can generate any other point in its subgroup over the elliptic curve by multiplying G by some integer in the range [0...r]. 
The number r is called "order" of the cyclic subgroup (the total number of all points in the subgroup).
```

Why " if the group is small, the security is weak. "

```
go through
```



How to get new point on the curve

```
add to itself
G+G = 2G
```

Base point

```
y²=x³+ax+b (mod p)
```

```
a= 2
b= 3
p= 97
n= 18
x-point= 3
P (3,91) Point is on curve
2P (80,87) Point is on curve
3P (80,10) Point is on curve
4P (3,6) Point is on curve
5P=0
6P (3,91) Point is on curve
7P (80,87) Point is on curve
8P (80,10) Point is on curve
9P (3,6) Point is on curve
10P=0
11P (3,91) Point is on curve
12P (80,87) Point is on curve
13P (80,10) Point is on curve
14P (3,6) Point is on curve
15P=0
16P (3,91) Point is on curve
17P (80,87) Point is on curve
18P (80,10) Point is on curve
```

```
We can see that this is a bad base point, as it will cycle.
```

```
So, in real-life, when we select a base point, we make sure that it has a high order value, so that it does not cycle. 
```

For SEPC256k1, we have a base point and prime number of:

```
x = 0x79BE667EF9DCBBAC55A06295CE870B07029BFCDB2DCE28D959F2815B16F81798
y = 0x483ADA7726A3C4655DA4FBFC0E1108A8FD17B448A68554199C47D08FFB10D4B8
p = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFEFFFFFC2F
order = FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFEBAAEDCE6AF48A03BBFD25E8CD0364141
```

> Note
>
> (x,y) is a base point
>
> p is for mod
>
> order is the total amount of the points in a group

Select generator

```
Note
that if we take the point {5, 9} as generator, 
it will generate just 3 EC points: {5, 8}, {5, 9} and infinity. 
Because the curve order is not prime number, different generators may generate subgroups of different order. 
This is a good example why we should not "invent" our own elliptic curves for cryptographic purposes and we should use proven curves.
```

Public key and private key

```python
from tinyec import registry
import secrets

curve = registry.get_curve('secp192r1')

privKey = secrets.randbelow(curve.field.n)
pubKey = privKey * curve.g
print("private key:", privKey)
print("public key:", pubKey)
```

```
output:
private key: 4225655318977962031264230130242180748818603147467615868902

public key: (5396030834456770190396776530938374882273836179487834152291, 3422160588166914010077732710830109086004758012634997793937) 
on "secp192r1" => y^2 = x^3 + 6277101735386680763835789423207666416083908700390324961276x + 2455155546008943817740293915197451784769108058161191238065 
(mod 6277101735386680763835789423207666416083908700390324961279)
```

> Note
>
> private key is really just a integer (and you will get it with different value every time)
>
> don't worry about the memory it allocated and it's calculation 
>
> private is just a random integer from 0 to 2^256
>
> "g" is the base point -- generator according to the standard like 'secp192r1'
>
> base point is fixed

```python
print(type(privKey))

output:
<class 'int'>
```

```
Note that in real projects, 192-bit curves are considered weak, so 256-bit curves are recommended (or more bits), where the keys are also 256-bits (or respectively more). We use 192-bit curve in the above example just to make the sample output smaller.

---'secp192r1' and secp256k1'
```

How to get my own private key



What is RSA



How public and private encrypt data