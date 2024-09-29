---
title: s
date: 2024-09-29T02:37:38.504Z
---

# 给对象动态添加属性
```python
class Student(object):
    def __init__(self, name):
        self.name = name

student = Student('feng')
print(student.name)

student.age = 19
print(student.age)
```

python的对象可以动态添加实例方法，实例变量。

即如果类本身没有定义这个实例变量，但可以在创建对象后，动态给这个创建后的对象添加实例变量并且赋值（可以是方法，可以是值）。

如下，通过`student.age = 19`给Student添加本来没有的age属性。 
```python
student.age = 19
print(student.age)
```

# `__slot__`

```
如果要限制类实例动态添加实例域，需要用到`__slot__`关键字：
```python
class Student(object):
    __slots__ = ('name', 'age')
    def __init__(self, name, age, city):
        self.name = name
        self.city = city

student = Student('feng',18, 'Guangzhou')
print(student.name)
print(student.age)
print(student.city)
```
上面这段代码限制了Student类对象只能有name,age这两个属性，否则报错。
AttributeError: 'Student' object has no attribute 'city'

