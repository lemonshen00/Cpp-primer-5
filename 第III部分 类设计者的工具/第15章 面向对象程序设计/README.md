# 第15章 面向对象程序设计

## 15.1 OOP：概述

面向对象程序设计（object-oriented programming）的核心思想是数据抽象（封装）、继承和动态绑定（多态）。

### 继承
通过继承（inheritance）联系在一起的类构成一种层次关系。通常在层次关系的根部有一个基类（base class），其他类则直接或间接地从基类继承而来，这些继承得到的类叫做派生类（derived class）。基类负责定义在层次关系中所有类共同拥有的成员，而每个派生类定义各自特有的成员。

对于某些函数，基类希望它的派生类各自定义适合自身的版本，此时基类应该将这些函数声明为虚函数（virtual function）。方法是在函数名称前添加`virtual`关键字。

```C++
// 书店中的书籍有不同的定价策略，Quote表示基类
// isbn（），返回书籍中的ISBN编号。该操作不涉及派生类的特殊性，因此只定义在Quote类中
// net_price（size_t），返回书籍的实际价格，前提是用户购买该书的数量达到一定标准。这个操作是类型相关的，因此基类/派生类都应该包含该函数。
class Quote
{
public:
    std::string isbn() const; // const，函数不修改数据成员
    virtual double net_price(std::size_t n) const;  // const，函数不修改数据成员
};
```
