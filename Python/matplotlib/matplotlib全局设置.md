##### 1. 调用属性字典plt.rcParams.keys()的方法查看并设置matplotlib全局属性
plt.rcParams.keys()可以查看matplotlib的全局属性，但是这个目前看来只是在控制台中有效，在script区域显示不出来
查看目前状态之后，将所有要修改的属性设置成一个属性字典，再把这个字典传递给plt.rcParams.update更新已经修改的属性
```Python 
parameters = {'xtick.labelsize': 16,
              'ytick.labelsize': 16,
              'font.family':'SimHei',
              'axes.unicode_minus':False}
plt.rcParams.update(parameters)

```
plt.rcParams.keys()的属性完全可以现学现用

##### 2.以mpl.rc()的方式针对单个参数进行修改
matplotlib.rc()的修改方法类似从plt.rcParams.keys()调用一个ob:attr对象，以str形式指定ob对象，再以实名参数的实行向其attr传递值，适用于参数较少或设置单个属性的情况
``` Python
mpl.rc("font",family='SimHei')
mpl.rc("axes",unicode_minus=False)

```
或先将要传递的参数定义成一个dict，再以"\*****dict"的方式调用，适用于属性较多或需要大量设置的情况
``` Python
font={"family":'SimHei'}
axes={"unicode_minus":False}

mpl.rc("font",**font)
mpl.rc("axes",**axes)

```

##### 3. plt.style.use设置图的风格
使用plt.style.use设置图片的风格，统计图形可以选择ggplot风格，反正统计这块跟着R语言走不会有大错
关于其它plt.style.use的可选值如下
``` Python
print(plt.style.available) # 打印样式列表

['bmh', 'classic', 'dark_background', 'fast', 
'fivethirtyeight', 'ggplot', 'grayscale', 'seaborn-bright', 
'seaborn-colorblind', 'seaborn-dark-palette', 'seaborn-dark', 'seaborn-darkgrid',
 'seaborn-deep', 'seaborn-muted', 'seaborn-notebook', 'seaborn-paper', 
'seaborn-pastel', 'seaborn-poster', 'seaborn-talk', 'seaborn-ticks',
 'seaborn-white', 'seaborn-whitegrid', 'seaborn', 'Solarize_Light2', 
'tableau-colorblind10', '_classic_test']

```