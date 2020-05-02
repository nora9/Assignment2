# how to solve [Assignment2](https://github.com/nora9/Assignment2/blob/master/assignment2.py):
## [Decryption function](https://github.com/nora9/Assignment2/blob/master/assignment2.py)
the main idea is reverse the [Encryption function](https://github.com/nora9/Assignment2/blob/master/encrypt.py) process

first step:

write F(w) as the same in the [Encryption function](https://github.com/nora9/Assignment2/blob/master/encrypt.py)

```python
def F(w):
	return ((w * 31337) ^ (w * 1337 >> 16)) % 2**32
```

second step:

writing decrytion function by reversing the two steps in the [Encryption function](https://github.com/nora9/Assignment2/blob/master/encrypt.py) and repeat these 32 times

1-
```python
tempa = a
        d = d ^ 1337
        a = c ^ (F(d | F(d) ^ d))
        b = b ^ (F(d ^ F(a) ^ (d | a)))
        c = tempa ^ (F(d | F(b ^ F(a)) ^ F(d | b) ^ a))
```

2-
```python
tempa = a
a = d ^ 31337
d = c ^ (F(a | F(a) ^ a))
c = b ^ (F(a ^ F(d) ^ (a | d)))
b = tempa ^ (F(a | F(c ^ F(d)) ^ F(a | c) ^ d))
```

third:

read the encrypted message from the [flag](https://github.com/nora9/Assignment2/blob/master/flag.enc) file

```python
ct = open(r"flag.enc","rb").read()
```

fourth:

decrypt the message and then display the result
```python
pt = "".join(decrypt(ct[i:i+16]) for i in range(0,len(ct), 16))
print (pt)
```

fifth:

submit result

[my submission](https://github.com/nora9/Assignment2/blob/master/1.png)

[my profile](https://github.com/nora9/Assignment2/blob/master/2.png)
