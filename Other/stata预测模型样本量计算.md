安装：
``` stata
ssc install pmsampsize
```
（1）目标值是连续变量

``` stata
pmsampsize, type(c) rsquared(0.9) parameters(20) intercept(26.7) sd(8.7)
```
Type: 计算类型，c是连续变量，s是时序变量，b是二分类变量

rsquared： 期待的R方值

parameters：参与建模的特征数量

intercept：目标变量平均值

sd：目标变量标准差




（2）目标值是时序变量（cox）

``` stata
pmsampsize, type(s) rsquared(0.051) parameters(40) rate(0.6) timepoint(7) meanfup(2.07)
```

rate：结局事件发生率

timepoint：要观测的时间距离（年）

meanfup：目标样本的平均随访时间


（3）目标值是二分类变量

``` stata
pmsampsize, type(b) rsquared(0.05) parameters(20) prevalence(0.67)
```

prevalence：观测结局的发生比例
