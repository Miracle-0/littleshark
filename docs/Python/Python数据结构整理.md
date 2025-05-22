# 数据结构汇总

## 列表 list

```python
a=[] #set up an empty list
a=[2,3,5,7,11]

#插入
a.append(13) #append item，加在末尾
a.extend("ab") #逐一加入
a.insert(2,4) #位置2，放4

#输出
print(a) #[2,3,5,7,11]
print(*a) # 2 3 5 7 11
print(a.index(2)) #输出2的index

slen = len(a)
smin = min(a)
smax = max(a)
ssum = sum(a)

#删除
a.remove(5) #删掉第一个出现的5
#如果要删掉所有，用 for i in a[:]，这样会生成一个副本，删除在原列表，就不影响了
a.pop(2) #删掉下标为2的东西，默认为最后一项

for i in a #遍历

a.reverse() #反转
a.sort() #默认为升序，降序改为a.sort(reverse=True)

#推导式
nl = [2*number for number in [1,2,3,4,5]] #基本，得[2, 4, 6, 8, 10]
nl = [number for number in range(1,8) if number%2==1] #条件过滤，得1,3,5,7

#难题:从外往里看，有括号加括号
mat=[[i*3+j+1 for j in range(3)] for i in range(5)]
mattrans=[[row[col] for row in mat] for col in range(3)]
print(mat) #[[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15]]

#构建二维数组存矩阵
m = int(input("请输入矩阵的行数: "))
n = int(input("请输入矩阵的列数: "))
matrix = []
for i in range(m):
    row = list(map(int, input().split()))
    matrix.append(row)
print(matrix)

#矩阵转置
matrix1 = []
for i in range(n):
    row = [matrix[j][i] for j in range(n)]
    matrix1.append(row)
```

<img src="D:\Typora\picture\image-20250408110403767.png" alt="image-20250408110403767" style="zoom: 25%;" />

<img src="D:\Typora\picture\image-20250407231226959.png" alt="image-20250407231226959" style="zoom: 33%;" />



## 元组 tuple

> [!NOTE]
>
> 1. 不可修改
> 1. 用（），比如（1,3,4.0,7）
> 1. 优点
>    1. 速度比列表快
>    1. 不可修改，所以可以作为字典的键
>    1. 适用场景:存储常量数据､字典键､函数返回值等需保证数据完整性的场景｡

```python
d = (100,20) #创建
d.count(100) #100出现的次数
d.index(20) #20的index
```



## 字符串

| ![image-20250407232018638](D:\Typora\picture\image-20250407232018638.png) |      | ![image-20250407232101119](D:\Typora\picture\image-20250407232101119.png) |      |
| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ---- |

加密

<img src="D:\Typora\picture\image-20250515224233137.png" alt="image-20250515224233137" style="zoom: 50%;" />

```python
table = [chr(i) for i in range(ord('A'), ord('Z'))]
new_table = table[:2]+table[2:]
s = input()
news = [new_table[table.index(i)] for i in s]
print(' '.join(news))
```



> [!NOTE]
>
> **join**
>
> 特别注意输出，比如result = ' '.join(set/list)，这样可以避免最后输出多的空格



## 集合 set

> [!NOTE]
>
> 1. 值不重复，会去重

```python
#创建
fruit = {"apple","banana","pie"} #创建集合

#添加
fruit.add("orange") #添加单个元素
fruit.update("kiwi fruit", "pineapple") #多个元素

#删除
fruit.discard() #如果存在则删除，不存在无效果
fruit.remove() #如果存在则删除，不存在会抛出异常
fruit.pop() #如果存在删除任意一个元素并返回，不存在会抛出异常
fruit.clear() #删除所有元素，剩下一个空集合

#子集subset与超集superset
s1.issubset(s2) #是否为子集
s2.issuperset(s1) #是否为超集

#集合比较 == !=  < <= > >=

s1|s2 #并集  或者s1.union(s2)
s1&s2 #交集
s1-s2 #差集
```



## 字典

```python
students = {} #设为空
students = {134342:'张三', 3244235:"李四"} #创建字典

#访问
students.keys() #返回所有键key
score[134342] #返回对应的值value
score.get('134342') #同上，如果找不到会报错
score.items() #返回所有内容

#修改和增加
student[134342] = '王五' #修改，若没有则添加
student.update({13323:'许六'})

#删除
del student[134342]
student.pop(134342)  #有返回值
student.clear()

len(student)  #返回字典条目数量

#遍历
for name in student:
    print(f"{name}:{student[name]}")
```

> [!IMPORTANT]
>
> ![image-20250408105728281](D:\Typora\picture\image-20250408105728281.png)



### 字典Plus：分支先变成查表，进一步优化表，把它变成字典等型式

<img src="D:\Typora\picture\image-20250411203555720.png" alt="image-20250411203555720" style="zoom:33%;" />

```python
import math
a = input().split() #得到字符串
w = math.ceil(float(a[1]))
f = {"TC":[10,2,{"Y":5,"N":0}], "SN":[12,3,{"Y":6,"N":0}], "SW":[20,5,{"Y":10,"N":0}]}
cost = f[a[0]][0]+f[a[0]][1]*(w-1)+f[a[0]][2][a[2]] #f[a[0]]负责选到字典的值
```

> [!IMPORTANT]
>
> 需要加强训练，不然后果严重，而且可以减少你写if语句



### 字典plus

<img src="D:\Typora\picture\image-20250411213552201.png" alt="image-20250411213552201" style="zoom:33%;" />

```python
#输入处理
def myinput(poly_str):
    poly_dic = {}
    for term in poly_str: #取出列表中的每一项★
        coef, exp = map(int, term.split()) 
        poly_dic[exp] = coef #字符串改字典★
    return poly_dic

p = input().split(',')
g = input().split(',')
que = int(input())

dic_p = myinput(p)
dic_g = myinput(g)

poly1 = {5:5,3:6,1:-10,0:-2}
poly2 = {5:7,4:3,2:-8,0:10}
poly = {} #放取的和
deg = set(poly1.keys()) | set(poly2.keys()) #取出和，看他们相同的部分
for i in deg:
    coeff=poly1.get(i,0)+poly2.get(i,0)  #用get，避免找不到之后报错
    if coeff!=0: #避免取和以后系数为0
        poly[i]=coeff #添加项
```

find() 字符串

in：列表

get：字典
