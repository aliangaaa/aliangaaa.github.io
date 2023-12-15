```cpp
connect(dynamiccast<A*>(a), static_cast<void (A::*)(QString)>(&A::b),[]{}() );

connect(dynamiccast<A*>(a), QOverload<QString>::of(&A::b),[]{}() );
```

qt 5.5 跨库用信号使用qt5的连接方式会出现multiple definition错误
