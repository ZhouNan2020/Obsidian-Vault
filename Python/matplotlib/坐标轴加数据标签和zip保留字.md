matplotlib给plot中加数据标签的基本思想是，遍历构成图的数据，使用plt.text将标签放置在合适的位置，其中需要用到zip保留字。
zip保留字解释如下：
``` python
# zip()函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。
a = [1,2,3]  
b = [4,5,6]  
c = [4,5,6,7,8]  
zipped = zip(a,b)     # 返回一个对象  
zipped  
<zip object at 0x103abc288>  
list(zipped)  # list() 转换为列表  
[(1, 4), (2, 5), (3, 6)]  
list(zip(a,c))              # 元素个数与最短的列表一致  
[(1, 4), (2, 5), (3, 6)]

a1, a2 = zip(*zip(a,b))      # 与 zip 相反，zip(*) 可理解为解压，返回二维矩阵式  
list(a1)  
[1, 2, 3]  
list(a2)  
[4, 5, 6]
```
在mpl中，zip用来将不同数据轴的数据集合打包，并以一一对应的方式返回，这返回的元组便可用于plt.text的定位，如下例
``` python
x = most_common_herb1['herb']
y = most_common_herb1['count']
y = list(y)
y.reverse()  # 倒序
ax1.barh(x, y, align='center', color='dodgerblue', tick_label=list(x))
ax1.margins(y=.01, x=.01)
ax1.ignore_existing_data_limits = True
ax1.autoscale_view(tight=False, scalex=False, scaley=True)
for a,b in zip(x,y):
	plt.text(b+0.1,a,b,ha = 'center',va = 'center',fontsize=14)
```
这是一个残例，most_common_herb1是一个表示草药与草药计数的矩阵，绘制成barh，所以变量名为y轴，而变量值为x轴，因此在将a，b值从zip后的x值和y值中取出后，在定位时颠倒了a和b的值，以b（变量的y值）定位text的x值，a（变量的x值）定位text的y值。plt.text还有其它几个参数如下：
``` python
plt.text(x, y, s, fontsize, verticalalignment,horizontalalignment,rotation , **kwargs)
```

-   x,y表示标签添加的位置，默认是根据坐标轴的数据来度量的，是绝对值，也就是说图中点所在位置的对应的值，特别的，如果你要变换坐标系的话，要用到transform=ax.transAxes参数。
-   s表示标签的符号，字符串格式，可以在在遍历zip得到的元组中取值
-   fontsize顾名思义就是你加标签字体大小了，取整数。
-   verticalalignment表示垂直对齐方式 ，可选 'center','top','bottom','baseline'等
-   horizontalalignment表示水平对齐方式 ，可以填 'center','right','left'等
-   rotation表示标签的旋转角度，以逆时针计算，取int值
-   后面还有 family 用来设置字体，style 设置字体的风格，weight 字体的粗细, bbox 给字体添加框,如 bbox=dict(facecolor=‘red’, alpha=0.5) 等，各种风格，应有尽有，总有一款适合你。

