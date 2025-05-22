# 函数

## 内置函数

### enumerate(iterable, start=0)

相比直接遍历，可以得到下标

```python
for i, fruit in enumerate(["apple","banana"], start=1):
    print(f"第{i}个水果：{fruit}")

#Start负责i的计数
#第1个水果：apple
#第2个水果：banana

{i:key for i,key in enumerate("Python")}
#{0: 'P', 1: 'y', 2: 't', 3: 'h', 4: 'o', 5: 'n'}
```



### sorted(iterable, key, reverse)

sort(list特有)无返回值，会直接改变原列表

sorted（是内置函数）有返回值，不改变原对象

```python
sorted(students, key=lambda s : s[1], reverse=True)
#key是按什么排序，类似一个指针
#lambda是临时函数，此处就是指对于每一个元素，取它的第二个
#reverse就是问是否翻转，默认是升序
```



### zip()

<img src="D:\Typora\picture\image-20250423173013096.png" alt="image-20250423173013096" style="zoom:50%;" />

<img src="D:\Typora\picture\image-20250423173043914.png" alt="image-20250423173043914" style="zoom:50%;" />

<img src="D:\Typora\picture\image-20250423173119227.png" alt="image-20250423173119227" style="zoom:50%;" />

![image-20250423173128419](D:\Typora\picture\image-20250423173128419.png)



### map(fun, element)

对可迭代对象中每一个元素去调函数（注：不用加括号）

```python
list(map(int, input().split()))

list(map(lambda x,y:x+y, [1,3,5,7,9],[2,4,6,8,10]))
#[3,7,11,15,19]
```



## 自定义函数

```python
def size(a):  #注意加冒号
    result = a*a
    return result

#传参
def demo(name,age):
    print(...)
    return None
    
demo("Jack",19)
demo(age=19, name='Jack')
```

![image-20250423173356688](D:\Typora\picture\image-20250423173356688.png)

![image-20250423174153725](D:\Typora\picture\image-20250423174153725.png)

例1：计算多项式

```python
def polyvalue(lst,x):
    result = 0
    for i in range(len(lst)):
        result+=lst[i]*x**i
    return result
```

例2：输出10个不重复的英文字母

> 随机输入一个字符串，把最左边的10个不重复的英文字母（不区分大小写）挑选出来。
> 如没有10个英文字母，显示信息“not found”

```Python
s = input()
b = []
for i in s:
    if i.isalpha() and (i.upper() not in b) and i.lower() not in b:#也可以用'A'<=i<='Z' or 'a'<=i<='z'，或者用ord进行比较
        b.append(i)
    if len(b)>=10:
        break
if len(b)==10:
    print(*b) #此处亦可用" ".join(b[:10])
else:
    print("not found")
```



## 模块化编程

直接调用标准库函数

### 导入方式

```python
import math_tools #全量导入
from math_tools import PI#PI精准导入
import math_tools as mt #别名导入
from tools.math_tools import circle_area #包内导入 多级包
```

### 示例：random

```python
import random
#生成随机浮点数
random.random() #0.8639550729865918 产生0-1之间的浮点数，不添加参数
random.uniform() #7.751233114562459 范围内浮点数
#生成随机整数
random.randint(20,30) #范围内生成随机数
random.randrange(10,30,2) #最后一位是步长
#抽排&洗牌
lst=[3,10,9,2]
random.choice(lst) #抽牌：要求可通过下表访问
random.shuffle(lst) #洗牌，会改变原序列
#抽样
random.sample("This is a sample",5) #['p', ' ', 'T', 'h', 'e']
random.sample([3,10,9,2],3) #序列取样亦可
```

应用

```python
#抛硬币
import random
lst = [random.randint(0,1) for i in range(100)]
print(f"{sum(lst)}/{len(lst)}={sum(lst)/len(lst):.2f}")
```

```Python
#蒙特卡罗法求圆周率
import random
import math

incide=0
samples=10000
for i in range(samples):
    x = random.random()
    y = random.random()
    
    if x**2+y**2<=1:
        incide+=1 
pi = incide/samples*4
print(pi)
```

<img src="D:\Typora\picture\image-20250514174755035.png" alt="image-20250514174755035" style="zoom:33%;" />

作用域：优先局部，后全局

函数默认参数是会改变的
