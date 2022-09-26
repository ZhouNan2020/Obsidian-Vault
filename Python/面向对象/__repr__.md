这是一种可用于通用输出打印的工具，可以调用任何<u>内省工具或任何方法</u>的结果进行打印输出。
仍然以继承类的代码举例：
``` python
class Father:
    def __init__(self,name,age,pay):
        self.name = name
        self.age = age
        self.pay = pay
    def raisePay(self,percent):
        self.pay = int(self.pay*(1.0 + percent))
        return self.pay

class child(Father):
    def __init__(self,name,age,pay,bonus):
        Father.__init__(self,name,age,pay)
        self.bonus = bonus    
    def raisePay(self,percent,bonus):
        Father.raisePay(self,percent + bonus)
        return self.pay
    def __repr__(self):
        return '%s after raise:%s' % (self.name,self.raisePay(0.1,0.1))
```
我们在子类child中添加了__repr__方法，该方法返回一句话显示某人在涨薪后的薪水。使用“%s“定义需要填补的字符串空位，打印主体与赋值内容之间以%分开，按照顺序将值传递给打印主体。
``` python
Bom=child('Bom',50,50000,0.1)
print(Bom.__repr__())
```
输出为
``` python
Bom after raise:72000
```