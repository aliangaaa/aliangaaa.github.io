```python
import os
import argparse

parser = argparse.ArgumentParser(description='test')
parser.add_argument('-con', dest='content', type=str, help='content to write')
parser.add_argument('-cnt', dest='cnt', type=int, help='write cnt')
args = parser.parse_args()

if __name__ == '__main__':
    # 打开（或创建）一个文本文件
    file = open('example.txt', 'w')
    # 写入内容到文件
    for i in range(0, args.cnt):
        file.write(args.content)
    # 关闭文件
    file.close()
```

[python之argparse模块常见用法包含实例(超详细)\_python argparse-CSDN博客](https://blog.csdn.net/RudeTomatoes/article/details/117003291)
