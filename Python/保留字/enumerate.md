enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

``` python
enumerate(sequence, [start=0])
```
例：
``` python
seq = ['one', 'two', 'three'] 
for i, element in enumerate(seq): 
	print(i, element)
```
output：
``` python
0 one
1 two
2 three
```
以非for方式呈现：
``` python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']  
list(enumerate(seasons))  
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]  
list(enumerate(seasons, start=1))       # 小标从 1 开始  
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```
