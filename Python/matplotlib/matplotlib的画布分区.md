###### 全局
``` Python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

x=np.linspace(1, 10)
y=np.sin(x)
y1=np.cos(x)
y2=np.tan(x)
```


##### 1. plt.subplot（）直接分color: 
使用subplot函数在画布上直接分区，subplot接受3个int作为参数，以下方代码为例，该代码将画布分为1行2列，第一个subplot的位置在第一个block，第二个subplot在第二个block。这种方法实现等分画布比较简单。
``` Python
plt.subplot(121)
plt.plot(x,y)

plt.subplot(122)
plt.plot(x,y1)

plt.show()

```
![[Pasted image 20220908210223.png]]

##### 2. plt.figure（）不等分画布
使用plt.figure先将画布实例化，然后使用fig.add_subplot()方法向画布添加图形，fig.add_subplot()同样接受3个int以确定位置，不同于subplot的是，add_subplot可以设置互相不依赖的坐标轴，从而实现对画布的自由划分。在下方代码中，ax1位于1行2列的画布中的第一个block，ax2位于2行2列画布中的第二个block，ax3位于2行2列画布中的第四个。
``` Python
fig=plt.figure()
ax1=fig.add_subplot(121)
ax1.plot(x,y)

ax2=fig.add_subplot(222)
ax2.plot(x,y1)

ax3=fig.add_subplot(224)
ax3.plot(x,y2)

```
![[Pasted image 20220908210251.png]]

##### 3. plt.subplot2grid()在网格布局上划分画布
plt.subplot2grid先将画布网格化，其关键参数包括两个tuple和两个行列参数，其中第一个tuple确认将画布分为几行几列的网格，本例中将画布分为2行3列，第一个scatter图放在标号为（0，0）的位置（python从0开始计数，因此第1行第1列的标号为0，0），第二个plot图放在标号为（0，1）的位置（即第1行第2列），colspan和rowspan两个函数为指定该图跨越几个网格，例如第一个scatter图跨越横向2个网格，纵向1个网格。根据测试，plt.subplot2grid()可以在同一张画布上画不同图形时按照不同的网格裁画布，目前已经获知的情报是，他会自动避开已经有图形的位置，裁剩余的空白画布，但经过测试发现仍然有潜在的、未被明确的工作机制。
``` Python
plt.subplot2grid((2,3),(0,0),colspan=1,rowspan=2)
plt.scatter(x,y)

plt.subplot2grid((2,3), (0,1),colspan=2)
plt.plot(x,y1)

plt.subplot2grid((2,3), (1,1),colspan=2)
plt.plot(x,y2)

```
![[Pasted image 20220908212828.png]]
##### 4. 使用plt.subplots创建一个带有多个子区的画布实例fig
plt.subplots返回值为一个（fig，ax）元组，其中fig是一个Figure画布对象，ax是一个np.array数组，数组的形状由plt.subplots划分画布的方法决定，例如本例中plt.subplots将画布分为2行3列，那么ax的形状就是2×3。在指定区域画图时，使用ax切片定位画布位置。plt.subplots有一个sharex或sharey的函数，接受布尔值，用于决定该画布上的所有图形是否共享x轴或y轴。
```Python
fig,ax=plt.subplots(2,3, sharey=True)
ax1=ax[0,0]
ax1.scatter(x,y)

ax2=ax[1,2]
ax2.plot(x,y1)

ax3=ax[0,2]
ax3.bar(x,y2)

```

![[Pasted image 20220908215424.png]]