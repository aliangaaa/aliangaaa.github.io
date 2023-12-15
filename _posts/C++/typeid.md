```cpp
class base
{
public :
    void m(){cout<<"base"<<endl;}
};
class derived : public base
{
public:
    void m(){cout<<"derived"<<endl;}
};

base * p = new derived;

运算								描述
typeid(p) == typeid(base*)			true
typeid(p) == typeid(derived*)		false
typeid(*p) == typeid(base)			true
typeid(*p) == typeid(derived)		false
```

```cpp
class base
{
public :
    virtual void m(){cout<<"base"<<endl;}
};
class derived : public base
{
public:
    void m(){cout<<"derived"<<endl;}
};

base * p = new derived;

运算								描述
typeid(p) == typeid(base*)			true
typeid(p) == typeid(derived*)		false
typeid(*p) == typeid(base)			false
typeid(*p) == typeid(derived)		true
```

[C++ typeid关键字详解-CSDN博客](https://blog.csdn.net/gatieme/article/details/50947821)

使用多种类型集中一个函数时，需要类中有虚函数

```cpp
void tst(a* tmp) {
    if (typeid(*tmp) == typeid(b))
        std::cout << "b" << std::endl;
    if (typeid(*tmp) == typeid(c))
        std::cout << "c" << std::endl;
}
a* test4 = new b;
tst(test4);
```

对于多个class类实例，有用
