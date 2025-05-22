# Python OOP

:warning:看一下类方法、pass、案例1、错题讲解

类 + 对象

封装（将function与类型集成） 多态（对不同类型对象进行相同操作，类似运算符重载） 继承（代码复用）



## 封装

### 基础

例1

```python
class Circle:
    def __init__(self, radius=1): #构造函数，注意：__init__，self（引用当前创造的对象）为固定的，radius=1为默认值，优先使用传入的
        self.radius = radius
    def area(self): #第一个参数必须是self
        return math.pi * self.radius**2
    def perimeter(self):
        return 2 * math.pi * self.radius
    
#调用
circle1 = Circle(5)
print(circle1.area())
print(circle1.perimeter())
```

例2

```python
class Student:
    def __init__(self, number, name): #这些只是参数
        self.number=number #这是属性
        self.name=name
        self.GPA=0
        self.Course_Grade={}
    def getinfo(self):
        return self.number,self.name #输出是元组
    
student = Student(12345678, "Lin")
print(student.getinfo())        
```

### 类属性(即类的一个属性，比如Student类中存学生数)

```python
class Circle:
    count = 0
    
    def __init__(self, radius = 1):
        self.radius = radius
        Circle.count += 1

circle1 = Circle(5)
circle1 = Circle(10)
print(Circle.count)
```

### 类方法:question:

```python
@classmethod
def get_circle_count(cls):
    return cls.count

```

### pass语句

```python
class A:
    pass
```



## 继承：把父类给拿下来

示例1

```python
class Car():
    def __init__(self, name):
        self.name = name
        self.color = ""
    def setColor(self, color):
        self.color = color

class ECar(Car): #表示继承
    def __init__(self, name): #定义构造函数
        super().__init__(name) #按父类初始化，如果不加会被忽略。如果父类使用默认的构造函数，可以不写
        self.battery_size = 300
    def getEcar(self):
        print("Ecar "+self.name+" with battery of "+str(self.battery_size))
        
car = ECar("BYD")
car.getEcar()
```

示例2

```Python
import random
class Mylist(list):
    def choice(self):
        return random.choice(self)
    
lst = Mylist("good morning")
print(Mylist.__bases__)
print(lst.choice())
```



## 多态: 相同函数不同功能

```python
#继承
class Animal:
    def speak(self):
        return
class Dog(Animal):
    def speak(self):
        return "Woof!"
class Cat(Animal):
    def speak(self):
        return "Meow!"
#多态的体现
def animal_speak(animal):
    print(animal.speak())
    
Tom = Dog()
Alice = Cat()

animal_speak(Tom)
animal_speak(Alice)
```



## 案例:warning:补一下这个例子（分成两个文件，定义__str__）

```python
class BMI:
    def __init__(self, name, age, weight, height):
        self.name = name
        self.age = age
        self.weight = weight
        self.height = height
    
    def calculate_bmi(self):
        return self.weight/(self.height**2)
    
    def get_bmi_category(self):
        bmi = self.calculate_bmi()
        if bmi<18.5:
            return "thin"
        elif bmi<24:
            return "normal"
        elif bmi <28:
            return "fat"
        else:
            return "too heavy"
    
    def __str__(self): #类似于自定义输出
        return (f"BMI is {self.calculate_bmi()} and BMI category is {self.get_bmi_category()}")

if __name__=="__main__":#测试用，即只有该软件调用时有，别的import就不跑这段代码
    whale = BMI("whale", 20, 50, 1.67)
    print(whale)
```

