# 异常

## 区分

语法错误：代码写错了，编译出错，解释器能发现

异常：运行错误（如下标越界等）



## 基本结构

```python
try:
    #正常执行代码
except 异常情况1: 
    #处理异常1
except 异常情况2:
    #处理异常2
except: #所有异常，以上都不匹配（不推荐使用）
    #语句N
else: #无异常时使用（不一定要有）
    #语句N+1
finally: #无论是否异常都执行（不是必备，常用于释放资源，如关闭文件）
    #语句N+2
```



## 常见的异常类型

| 异常名称              | 描述                           |
| --------------------- | ------------------------------ |
| **TypeError**         | 无效类型操作，比如字符串加数字 |
| **ZeroDivisionError** | 0作为除数                      |
| NameError             | 访问未定义变量                 |
| IndexError            | 下标越界                       |
| KeyError              | 字典键不存在                   |
| ValueError            | 无效参数值                     |
| FileNotFoundError     | 打开不存在的文件               |



## 实例

```python
lists = [1,2,3]
try:
    position = int(input())
    print(lists[position]) #越界，出现IndexError
except IndexError:
    print(f"索引错误，索引范围为0-{len(lists)-1}")
except:
    print("出现未知错误")
else:
    print("一切正常")
finally:
    print("finally一直会执行")
    
#另一种写法，会帮你找错误，但不实用
#except Exception as e:
    #print("invalid input:", e)
```

