## General concept of python

`,` is the way to construct a tuple. So `a, b = 1, 2` in full form is `(a, b) = (1, 2)`. 

The speed  of `for` loop is low in python while fast in C. Since `map` funciton and `list comprehension` are written in C, refer to them instead of `for` loop will always improve performance and make the code pythonic. But there are cases where these two method give no obvious result.

`local variable` is faster then `global variable`. If you need to call a global variable in your function, it's better to copy it as a  local variable. Note the funciton name is a global variable.

The following codes illustrate the above opinion.

```
import time
x = 0
def doit1(i):
    global x
    x = x + i

list1 = range(100000)
t = time.time()     
for i in list1:         # Call function name in a global for loop.
    doit1(i)

print('time = ', time.time()-t)

>>> time =  0.08408689498901367
```
```
x = 0
def doit2(list_):
    global x
    for i in list_:     # Call for loop locally. 
        x = x + i       

t = time.time()
doit2(list1)

print('time = ', time.time()-t)

>>>time =  0.020014047622680664     # The speed is 4 times faster.
```
```
x = 0
def doit3(list_):
    global x
    x = sum(list_)     # Call the builtin sum function.
    print(x)           
t = time.time()
doit3(list1)

print('time = ', time.time()-t)

>>> time =  0.007987022399902344    # The speed is 10 times faster.
```

## Python Writing Style
http://docs.python-guide.org/en/latest/writing/style/

### The use of `blankline`:
1. There should be one `blank line` between two functions.
2. There shoould be two `blank line` between two classes.

### Docstring
http://www.python.org/dev/peps/pep-0257/
There are two forms of docstring: one-line docstring and multi-line docstrings.
For consistency, always use `'''xxxxx''''`, so you can expand it when necessary.

#### One-line docstring
```
def primes(n):
    '''Return True if the integer n is prime.'''
    if n is prime:
        return True
    else:
        return False
```
Note: 

1. One-line docstring should be one line. 
2. No black lines before and after the docstring.
3. The closing quotes are in the same line as teh opening quotes.
4. It's a command not a description; e.g, don't use `Returns ...`.

In order to keep a clear intent and a sustainable readability level, it is preferable to aviod returning meaningful values from many output points in the body.
```
def complex_function(a, b, c):
    if not a:
        return None  # Raising an exception might be better
    if not b:
        return None  # Raising an exception might be better
    # Some complex code trying to compute x from a, b and c
    # Resist temptation to return x if succeeded
    if not x:
        # Some Plan-B computation of x
    return x  # One single exit point for the returned value x will help
              # when maintaining the code.
```
