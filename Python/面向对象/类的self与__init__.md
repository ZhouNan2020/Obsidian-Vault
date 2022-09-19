self: 调用类的实例本身
``` python
class name:
	def setname(self,name)
		self.name=name
```
👆这个名为name的类中有个setname方法，将传入的参数name赋予self.name，如果要调用这个方法
``` PYTHON
H1=name（）#实例化name类给H1
H1.setname('ZhouNan') #以实例名调用类name中的setname方法，并传递参数‘ZhouNan’
print(H1.name) #此时print（H1.name)等同于调用了neme，因为在setname方法中已经将name的值赋给了self.name，所以会得到’ZhouNan‘
```
注意：1）在使用setname方法传递参数之前，不可调用H1.name，否则会报错该值未定义
2）在所有的类中，self均指调用类的实例本身，因此在传递参数时无须传递给self，从第二个参数开始按顺序传递，或选择实名传递

`__init__`： 类的构造函数
``` python
class num:  
    def __init__(self,value,v):  
        lis=0  
        for i in range(1,5):  
            lis=lis+i  
        value=value+lis
        self.value = value+v  
    def sum(self):  
        return self.value
```
👆在修改后的类num中，内置了构造函数__init__，使得该函数实例可以接受直接传参，该参数将会被__init__拦截并应用于其所对应def方法。👇将类num实例化后，传参给value和v
``` python
a = num(1,120) # 将num实例化后，传递1给value，传递120给v，这里用了顺序传递的方法，也可以用实名传递
a.sum() # .sum()的值为131
```
注意：1）只有使用num()传递参数时，才会被__init__拦截并进行相应的运算，如果直接以下面方式赋值，则直接self.value的值而不经过运算
``` python
a=num（）# 实例化num()
a.value=1 # 直接定义a.value=1,即直接到了构造函数的最后一行
a.sum() #输出值为1
```
2）在上面例子中，self.value的值是可以经过运算的，其它类中也是如此