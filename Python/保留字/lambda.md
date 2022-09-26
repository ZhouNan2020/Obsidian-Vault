1. lambda定义：快速获得一个匿名函数


2. lambda基本结构：

``` python
lambda arguments : expression
```
arguments：函数参数
expression：函数表达式
例：👇这个lambda函数
``` python
x = lambda a : a + 10
print(x(5))
```
👇等同于下面这个常规函数
``` python
def x(a):
	a=a+10
	print(a)
```

3. lambda特征
- lambda可以接受多个函数参数


4. lambda实例
- 无参数的匿名函数
``` python
t = lambda : True # 分号前无任何参数 
t() 
True
# 等价于下面函数
def func(): 
	return True 
```