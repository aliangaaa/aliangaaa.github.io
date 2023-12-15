lower\_bound二分查找大于等于的元素

upper\_bound二分查找大于的元素

1、对于vector等可以任意位置获取的数据结构，std的二分和自身的二分无区别

```cpp
vector<int> vec{1,2,3,4,5};
int num = 5;
std::lower_bound(vec.begin(), vec.end(), num);
std::upper_bound(vec.begin(), vec.end(), num);
vec.lower_bound(num);
vec.upper_bound(num);
```

2、对于set等不可任意获取的数据结构，std的效率为O(n)，较低

```cpp
set<int> myset;
myset.lower_bound(num);
std::lower_bound(set.begin(), set.end(), num);
```

3、获取下标的位置用

```cpp
vector<int>::iterator ite = vec.begin();
int index = ite - vec.begin();
```

4、找到最大小于的数

map/set ------ 插入负数

```cpp
upper_bound(-num);
```

