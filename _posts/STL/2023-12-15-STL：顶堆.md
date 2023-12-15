大顶堆：(默认)

priority\<T, vector\<T>, less\<T>> pri

小顶堆：

priority\<T, vector\<T>, greater\<T>> pri

原地建堆

vector\<int> p

eg.

make\_heap(p.begin(), p.end()，greater<>()/\**camp()*\*自定义/)

pop\_heap(p.begin(), p.end())     //将第一个也是最大的元素移动到最后

改变头

p.back() =

push\_heap(p.begin(), p.end())   //释放恢复排序的信号
