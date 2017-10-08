@(Python)

1. Previous and next values inside a loop 【[link](https://stackoverflow.com/questions/1011938/python-previous-and-next-values-inside-a-loop)】
``` 
foo = somevalue
previous = next_ = None
l = len(objects)
for index, obj in enumerate(objects):
    if obj == foo:
        if index > 0:
            previous = objects[index - 1]
        if index < (l - 1):
            next_ = objects[index + 1]
```
2. Iterating over every two elements in a list 【[link](https://stackoverflow.com/questions/5389507/iterating-over-every-two-elements-in-a-list)】
```
from itertools import izip

def pairwise(iterable):
    "s -> (s0, s1), (s2, s3), (s4, s5), ..."
    a = iter(iterable)
    return izip(a, a)

for x, y in pairwise(l):
   print "%d + %d = %d" % (x, y, x + y)
```
3. Return the maximum of an array or maximum along an axis, **ignoring any NaNs.** 【[link](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanmax.html)】
```
>>> np.nanmax([1, 2, np.nan, np.NINF]) # np.NINF 是极小值
2.0
>>> np.nanmax([1, 2, np.nan, np.inf]) # np.inf 是极大值
inf
```
4. Python 编码
4.1 Python3对文本和二进制数据作了更为清晰的区分，文本总是str类型，编码方式是Unicode，二进制数据择优bytes类型表示。在2.7版本的代码中，可以通过unicode_literals来使用Python 3.x的新的语法：
```
from __future__ import unicode_literals # 必须放在文件开头
```
4.2 获取当前系统默认编码
```
import sys
print sys.getdefaultencoding()  #获取当前系统默认编码
```
 4.3 Python字符串的encode与decode研究心得——解决乱码问题【[link](http://blog.csdn.net/lxdcyh/article/details/4018054)】
在Windows命令行下的编码转换方式：
```
#!/usr/bin/env python  
#coding=utf-8  
s="中文"
if isinstance(s, unicode):  
	#s=u"中文"  
    print s.encode('gb2312')  
else:  
	#s="中文"  
    print s.decode('utf-8').encode('gb2312')  
```

5. rawinput与input的区别
