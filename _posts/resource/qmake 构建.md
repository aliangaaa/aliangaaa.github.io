Qt构建、运行、qmake的区别

qmake：根据实际环境创建项目文件.pro   并且运行qmake生成适当的Makefile

构建：构建是增量编译，只编译有变化部分

重新构建：是把所有部分都重新编译

运行: 有改动则根据已有的Makefile进行编译，执行构建和重新构建时如果没有Makefile，会根据.pro文件等生成Makefile后再编译

所以运行顺序应该是：qmake-构建-运行

// qmake 在pro或者rc有改动时才需要运行
