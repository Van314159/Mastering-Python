## General concept of python
python 的 for 循环 和 C 的 for 循环是完全不同层面的. C 的 for 循环速度飞快，而 python 的 for 循环速度缓慢. 而 map 函数 和 list comprehension 所用的循环就是 C 编写的. 所以， 尽量不要用 python 的 for 循环.

local variable 比 global variable 更快。比如你在函数里需要调用 global variable， 那最好先把它 copy 为 local variable。函数名是 global variable。

下面三段代码展示了上两段的含义.

```
import time
x = 0
def doit1(i):
    global x
    x = x + i

list1 = range(100000)
t = time.time()     # 直接在代码主体调用 for 循环.
for i in list1:
    doit1(i)

print('time = ', time.time()-t)

>>> time =  0.08408689498901367
```
