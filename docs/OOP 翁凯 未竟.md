# OOP 翁凯

## Introduction

### 动态规划内存

new：`new int`; `new int[10]`

delete：调用析构函数 

​	`delete p`; 用于删除单个对象

​	`delete[] p` 逐个析构



## OOP核心思想

### 对象是啥？好玄乎

以教室为例

先看有哪些对象：老师、学生、幕布、电脑
他们有哪些属性：有没有学过C语言、困不困
他们有哪些操作：学生听课、玩手机
他们之间的关系是什么：学生回答问题，老师提问

好处：学生这个个体可以**重复用**，可以用于吃饭的场景



## 封装：把类包装起来

### 思想：对象=属性+服务

蛋图：属性在里面，看不见；对外提供操作

对象之间的关系：说明what to do（即通过访问成员函数来调用）
进而画出UML（unifield Modeling Language, 即右图，用于说明需求）

具体实现：一个类放在两个文件：声明（放在`.h`）和定义（放在`.cpp`）
只有声明是可以看见的，而函数定义是不可见的

<img src="D:\Typora\picture\image-20250510214930369.png" alt="image-20250510214930369" style="zoom:25%;" />	<img src="D:\Typora\picture\image-20250510220129162.png" alt="image-20250510220129162" style="zoom:25%;" />

### 类是啥？Class

struct为了兼容C语言，默认public

```c++
struct Point {
    int x;
    int y;
    void print();
};

void Point::print() {
    printf("%d %d\n", x, y);
}

int main() {
    Point p;
    p.x = 10;
    p.y = 20;
    p.print();
    return 0;
}
```

### 如何包装呢？设置权限

如何实现上面那个蛋图呢？如何避免访问private？access control

1. public
1. private：只有初始化+类的成员函数能调用
1. protected：子类能调用（用不上）



## 继承



## 多态



## C++相关

### :: Resolver 预解释器

`this` 隐藏的指针

```cpp
class Person {
private:
    int age;  // 成员变量（当前对象的年龄）
public:
    // 构造函数：参数名与成员变量名相同，无返回值，必须用 this 区分
    Person(int age) {
        this->age = age;  // this->age 表示当前对象的成员变量，age 是参数
    }
    void print() {
        cout << this->age << endl;
    }
}
```

`void Point::move(int dx, int dy)`与`void Point::initialize(Point* this, int dx, int dy)`等价
Point是姓，initialize是名，两个凑一起组成函数名





引用文件：

```c++
#include <stdio.h> //直接去库里找，比较小
#include ".h" //比较大，先去文件所在的文件夹找，再去别的地方找
```


