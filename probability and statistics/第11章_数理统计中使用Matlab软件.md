# 第11章 数理统计中使用 Matlab 软件

---

## 序言

### 1.内容介绍

&emsp;&emsp;本章详细介绍了 Matlab 概述、箱线图、假设检验与方差分析，并对其原理与例题进行了一一阐述

### 2.理论目标

- 掌握数学建模的概念与计算机技术在数理统计中的应用
- 掌握 Matlab 中常用分布的有关函数
- 掌握 Matlab 箱线图定义与 boxchart 函数
- 掌握 Matlab 参数估计与假设检验
- 掌握 Matlab 一元与多元方差分析

### 3.实践目标

- 无

### 4.实践案例

- 无

### 5.内容目录

- 1.Matlab 概述
- 2.Matlab 箱线图
- 3.Matlab 假设检验
- 4.Matlab 方差分析

---

## 第01节 Matlab 概述

### 1.1 数学建模

&emsp;&emsp;随着科学技术的迅速发展，**数学模型（Mathematical Model)**、**数学建模（Mathematical Modelling)** 这两个词出现的频率越来越高，它们正在成为人们日常生活和语言交流中常见的术语

&emsp;&emsp;所谓数学建模，可以说它是一种数学思考方法，是对现实的现象通过智力活动构造出能抓住其重要性且有用的特征的数学表示，从科学技术、工程、经济、管理等角度看数学建模，就是用数学的语言和方法，通过抽象、简化建立能近似刻画并解决实际问题的一种有力的数学工具，简单地说数学模型就是对实际问题的一种数学表述. 具体一点说，数学模型是关于部分现实世界为某种目的的一个抽象的简化的数学结构，更确切地说，数学模型就是对于一个特定的对象为了一个特定目标，根据特有的内在规律，做出一些必要的简化假设，运用适当的数学工具，得到的一个数学结构，可以是数学公式、算法、表格、图示等

&emsp;&emsp;数学建模是沟通现实世界和数学科学之间的桥梁，是数学走向应用的必经之路. 众所周知，具有悠久历史的数学是各门自然科学、工程技术乃至社会科学的基础，是科技进步、经济建设和社会发展的重要工具. 但是，作为一门基础的自然科学和一种精确的科学语言，数学又是以极为抽象的形式出现的，如果人为地割断数学与现实世界的密切联系，这种抽象的形式就会掩盖数学的丰富内涵，并对数学的实际应用形成巨大障碍

&emsp;&emsp;用数学方法解决一个实际问题，不论这个问题是来自工程建设、经济管理、生物、医学、地质、气象，还是社会、金融领域乃至人们的日常生活当中，都必须在实际问题与数学之间架设一座桥梁
- 首先把这个实际问题转化为一个相应的数学问题，然后对这个数学问题进行分析和计算，最后将所求得的解答回归实际，检验能否有效地回答原先的实际问题
- 如果最后得到的结果在定性或者定量方面与实际情况有很大的差距，那就要修正所建立的数学模型，直到取得比较满意的结果为止

### 1.2 计算机技术在数理统计中的应用

&emsp;&emsp;随着现代科学技术的迅猛发展，人类社会已开始进人一个利用和开发信息资源的 **信息社会**

> 信息数据数量大、范围广、变化快，传统的人工处理手段无法适应社会经济高速发展对统计提出的要求，也难以提高数据处理的速度和精度

&emsp;&emsp;计算机技术在数理统计中的应用，主要是在统计信息的存贮和检索、统计资料的分析和检验等方面的应用，解决了统计工作中的难题.
不仅是在实际的技术和经济工作中要将计算机技术应用于数理统计，在学习概率论与数理统计课程的阶段，同样也需要应用计算机技术，掌握了计算机技
术在数理统计中的应用以后，分析和研究问题的能力将极大地提高，研究问题的规模、分析计算的效率将极大地提高

&emsp;&emsp; **Matlab 软件** 提供了一些专用的工具箱 (toolbox)，如统计工具箱(statistics toolbox)，其中包含了大量的函数，可以直接用于求解概率论与数理统计领域的问题，当然 MATLAB是可扩展语言，还可以通过编写一些程序解决很多问题

### 1.3 Matlab 中常用分布的有关函数

#### 1.3.1 几种常见分布及其命令字符

&emsp;&emsp;统计工具箱中有 $20$ 多种概率分布，几种常见分布及其命令字符见下表

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=9>
 <tr height=18>
  <td style='text-align: center;'><strong>常见分布</strong></td>
  <td style='text-align: center;'><strong>二项分布</strong></td>
  <td style='text-align: center;'><strong>泊松分布</strong></td>
  <td style='text-align: center;'><strong>均匀分布</strong></td>
  <td style='text-align: center;'><strong>指数分布</strong></td>
  <td style='text-align: center;'><strong>正态分布</strong></td>
  <td style='text-align: center;'><strong>$\chi^2$分布</strong></td>
  <td style='text-align: center;'><strong>$t$分布</strong></td>
  <td style='text-align: center;'><strong>$F$分布</strong></td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'><strong>命令字符</strong></td>
  <td style='text-align: center;'>$bino$</td>
  <td style='text-align: center;'>$poiss$</td>
  <td style='text-align: center;'>$unif$</td>
  <td style='text-align: center;'>$exp$</td>
  <td style='text-align: center;'>$norm$</td>
  <td style='text-align: center;'>$chi2$</td>
  <td style='text-align: center;'>$t$</td>
  <td style='text-align: center;'>$f$</td>
 </tr>
</table>

#### 1.3.2 五类函数及其命令字符

&emsp;&emsp;统计工具箱中对每种分布都提供了 $5$ 类函数，其命令字符见下表

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=6>
 <tr height=18>
  <td style='text-align: center;'><strong>函数</strong></td>
  <td style='text-align: center;'><strong>概率密度函数(分布律)</strong></td>
  <td style='text-align: center;'><strong>分布函数</strong></td>
  <td style='text-align: center;'><strong>分位点</strong></td>
  <td style='text-align: center;'><strong>均值与方差</strong></td>
  <td style='text-align: center;'><strong>随机数生成</strong></td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'><strong>命令字符</strong></td>
  <td style='text-align: center;'>$pdf$</td>
  <td style='text-align: center;'>$cdf$</td>
  <td style='text-align: center;'>$inv$</td>
  <td style='text-align: center;'>$stat$</td>
  <td style='text-align: center;'>$rnd$</td>
 </tr>
</table>

#### 1.3.3 概率密度函数(分布律)及其调用格式

&emsp;&emsp;Matlab 自带了一些常见分布的概率密度函数(分布律)，函数名称及调用格式见下表

<table border=0 cellpadding=0 cellspacing=0 width=1280 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=fixed>
 <tr height=18>
  <td style='text-align: center;'><strong>常见分布</strong></td>
  <td style='text-align: center;'><strong>二项分布</strong></td>
  <td style='text-align: center;'><strong>泊松分布</strong></td>
  <td style='text-align: center;'><strong>均匀分布</strong></td>
  <td style='text-align: center;'><strong>指数分布</strong></td>
  <td style='text-align: center;'><strong>正态分布</strong></td>
  <td style='text-align: center;'><strong>$\chi^2$分布</strong></td>
  <td style='text-align: center;'><strong>$t$分布</strong></td>
  <td style='text-align: center;'><strong>$F$分布</strong></td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'><strong>命令字符</strong></td>
  <td style='text-align: center;'>$binopdf(x,n,p)$</td>
  <td style='text-align: center;'>$poisspdf(x,\lambda)$</td>
  <td style='text-align: center;'>$unifpdf(x,a,b)$</td>
  <td style='text-align: center;'>$exppdf(x,theta)$</td>
  <td style='text-align: center;'>$normpdf(x,\mu,\sigma)$</td>
  <td style='text-align: center;'>$chi2pdf(x,n)$</td>
  <td style='text-align: center;'>$tpdf(x,n)$</td>
  <td style='text-align: center;'>$fpdf(x,n,m)$</td>
 </tr>
</table>

#### 1.3.4 几种常见分布的上侧 $a$ 分位点的调用格式

&emsp;&emsp;分位点的调用格式，只需在上表中把 `pdf` 换成 `inv` 即可，几种常见分布的上侧 $a$ 分位点的调用格式见下表

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=5>
 <tr height=18>
  <td style='text-align: center;'><strong>分布名称</strong></td>
  <td style='text-align: center;'><strong>正态分布</strong></td>
  <td style='text-align: center;'><strong>$\chi^2$分布</strong></td>
  <td style='text-align: center;'><strong>$t$分布</strong></td>
  <td style='text-align: center;'><strong>$F$分布</strong></td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'><strong>上侧$a$分位点的调用格式</strong></td>
  <td style='text-align: center;'>$norminv(1-\alpha)$</td>
  <td style='text-align: center;'>$chi2inv(1-\alpha,n)$</td>
  <td style='text-align: center;'>$tinv(1-\alpha,n)$</td>
  <td style='text-align: center;'>$finv(1-\alpha,n,m)$</td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'><strong>上侧$a$分位点</strong></td>
  <td style='text-align: center;'>$z_{\alpha}$</td>
  <td style='text-align: center;'>$\chi^2_{\alpha}(n)$</td>
  <td style='text-align: center;'>$t_{\alpha}(n)$</td>
  <td style='text-align: center;'>$F_{\alpha}(n,m)$</td>
 </tr>
</table>

---

## 第02节 Matlab 箱线图

### 2.1 箱线图定义

&emsp;&emsp;对于给定数值数据，对应的箱线图显示 **中位数**、**下四分位数** 和 **上四分位数** 、任何 **离群值**（使用四分位差计算得出）以及不是离群值的最小值和最大值

![box](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/box.png)

- 框的 **中间线** 为样本 **中位数**，用 $m$ 表示

- 每个框的 **上边缘和下边缘** 分别表示 **上四分位数和下四分位数**，对于任意一组数据，将其按照从小到大按顺序排列后，第 $25\%$ 的数为上四分位数，第 $50\%$ 数为中位数，第 $75\%$ 数为下四分位数，顶部和底部边缘之间的距离表示 **四分位差**，用 **IQR** 表示

- **离群值** 是指距离框的顶部或底部超过 **1.5IQR** 的值

- **须线** 是延伸到每个框的上方和下方的线条，一条须线将 **上四分位数与最大非离群值** (不是离群值的最大值) 相连，另一条须线将 **下四分位数与最小非离群值** (不是离群值的最小值) 相连

> 缺口区域的顶部和底部边缘分别对应于 $m+(1.57IQR)/\sqrt{n}$ 和 $m-(1.57IQR)/\sqrt{n}$，其中 $m$ 是中位数、IQR 是四分位差、$n$ 是数据点数，不包括 NaN 值，缺口有助于比较多个箱线图中的样本中位数，当指定 'Notch','on' 时，boxchart 函数会在每个中位数周围创建锥形着色区域

### 2.2 boxchart 函数

&emsp;&emsp;在 Matlab 中，通过 boxchart 函数绘制箱线图

``` matlab
boxchart(ydata)
boxchart(xgroupdata,ydata)
boxchart(___,Name,Value)
boxchart(ax,___)
b = boxchart(___)
```

- `boxchart(ydata)` 为矩阵 ydata 的每列创建一个箱线图，如果 ydata 是向量，则 boxchart 只创建一个箱线图 <br>
  每个箱线图显示以下信息：中位数、下四分位数和上四分位数、任何离群值（使用四分位差计算得出）以及不是离群值的最小值和最大值
  
- `boxchart(xgroupdata,ydata)` 根据 xgroupdata 中的唯一值对向量 ydata 中的数据进行分组，并将每组数据绘制为一个单独的箱线图 <br>
  xgroupdata 确定每个箱线图在 x 轴上的位置，data 必须为向量，xgroupdata 必须与 ydata 长度相同
  
- `boxchart(____, Name, Value)` 使用一个或多个 名称-值 对组参数指定其他图选项 <br>
  例如可以通过指定 'Notch','on' 使用缺口来比较样本中位数，在所有其他输入参数之后指定 名称-值 对组参数
  
- `boxchart(ax,____)` 将图形绘制到 ax 指定的坐标区中，而不是当前坐标区 (gca) 中 <br> 
  参数 ax 可以置于前面的语法中的任何输入参数组合之前 `b = boxchart(____)` 返回 BoxChart 对象，创建箱线图后，使用 b 设置箱线图的属性

### 2.3 Matlab 示例

- 随机产生一组 $[0, 1000]$ 的整数

``` matlab
clc 
clear all
close all
a = randi([0 1000], 40, 2);
boxchart(a);
```

![demo_1](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_1.png)

- 为了产生 **离群值** 向上和向下分别产生几个较大和较小的数

``` matlab
clc
clear all
close all
a = randi([0 1000], 40, 2);
a(41:44,1:2) = randi([1000 2000],4,2);
a(45:48,1:2) = randi([-1000 0],4,2);
boxchart(a);
```

![demo_2](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_2.png)

- 这里将所有原始数据点都在图中画出来以作比较

> 注意这里的横坐标是 **categorical 类型数据**，例如 0/1，high/low，long/short 等

``` matlab 
clc 
clear all
close all
a = randi([0 1000], 110, 1);
a(101:105,1) = randi([1000 2000],5,1);
a(106:110,1) = randi([-1000 0],5,1);
x = int16(rand(110,1));
x = categorical(x);
boxchart(x,a);
hold on
plot(x,a,'x');
```

![demo_3](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_3.png)

- 通过返回 **句柄**，可以产看箱线图的属性，并可以对很多属性进行自定义修改，例如离群值的颜色、大小、类型，框的颜色，须线的颜色、粗细、类型等

``` matlab
clc 
clear all
close all
a = randi([0 1000], 110, 1);
a(101:105,1) = randi([1000 2000],5,1);
a(106:110,1) = randi([-1000 0],5,1);
x = int16(rand(110,1));
x = categorical(x);
b = boxchart(x,a);
b.MarkerStyle = '+';
b.MarkerColor = 'r';
b.BoxFaceColor = [0.5 0.1 0.9];
b.WhiskerLineColor = [0.2 0.6 0.4];
```

![demo_4](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_4.png)

- 通过将 `Notch` 设置为 `on`，可以显示 **缺口区域**，用于比较中位数值是否彼此存在显著差异

``` matlab
b.Notch = 'on';
```

![demo_5](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_5.png)

- 当离群值的点比较多时，会彼此遮挡不利于观察，可在句柄中打开 `JitterOutliers`，使得点可以随机左右移动，同时可以更改点的属性

``` matlab
b.JitterOutliers = 'on';
b.MarkerStyle = 's';
```

![demo_6](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_6.png)

![demo_7](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/demo_7.png)

---

## 第03节  Matlab 假设检验

### 3.1 正态总体参数的检验

#### 3.1.1 总体均值的检验

&emsp;&emsp;Matlab 统计工具箱中的 **ztest 函数** 可用来作总体标准差已知时的单个正态总体均值的检验，对于假设检验 <br><br>
<center>$H_0:\mu=\mu_0=100,\quad H_1:\mu\ne\mu_0$</center><br>

```matlab
%定义样本观测值向量
x=[97 102 105 112 99 103 102 94 100 95 105 98 102 100 103];

%调用ztest函数作总体均值的双侧检验
%返回变量h，检验的p值，均值的置信区间muci,检验统计量的观测值zval
[h,p,muci,zval]=ztest(x,100,2,0.05)

%均值为100，标准差为2
```

- 若为单侧检验 

<center>$H_0:\mu\ge\mu_0=100,\quad H_1:\mu<\mu_0$</center>

``` matlab
%定义样本观测值向量
x=[97 102 105 112 99 103 102 94 100 95 105 98 102 100 103];

%调用ztest函数作总体均值的单侧检验
%返回变量h，检验的p值，均值的置信区间muci,检验统计量的观测值zval
[h,p,muci,zval]=ztest(x,100,2,0.05,'right')
```

&emsp;&emsp;**ttest 函数** 用来作总体标准差未知时的正态总体均值的检验

``` matlab
x=[49.4 50.5 50.7 51.7 49.8 47.9 49.2 51.4 48.9];

%调用ttest函数作总体均值的双侧检验
%返回变量h，检验的p值，均值的置信区间muci，结构体变量stats
[h,p,muci,stats]=ttest(x,50,0.05)
h = 1
p = 1.8775e-16
muci = 98.6579  103.6087
stats = 
    tstat: 44.3039
    df: 14
    sd: 4.4700

```

- 总体标准差未知时两个正态总体均值的比较 $t$ 检验，可以使用 **ttest2 函数** 进行

``` matlab
%第一组样本观测值向量
x=[20.1  20 19.3 20.6 20.2 19.9 20 19.9 19.1 19.9];

%第二组样本观测值向量
y=[18.6 19.1 20 20 20 19.7 19.9 19.6 20.2];

alpha=0.05; %显著性水平为0.05
tail='both'; %尾部类型为双侧
vartype='equal'; %方差类型为等方差

%调用ttest2函数作两个正态总体均值的比较检验
%返回变量h，检验的p值，均值差的置信区间muci，结构体变量stats
[h,p,muci,stats]=ttest2(x,y,alpha,tail,vartype)
```

#### 3.1.2 总体方差的检验

&emsp;&emsp;总体均值未知时的单个正态总体方差的 $\chi^2$ 检验,可用 **vartest 函数** 完成 <br><br>
<center>$H_0:\sigma^2=\sigma^2_0=1.5\quad H_1:\sigma^2\ne\sigma^2_0$</center>

``` matlab
x=[49.4 50.5 50.7 51.7 49.8 47.9 49.2 51.4 48.9];
var0=1.5; %原假设中的常数
alpha=0.05;%显著性水平为0.05
tail='both'; %尾部类型为双侧

%调用vartest函数作单个正态总体方差的双侧检验
%返回变量h,检验的p值，方差的置信区间varci,结构体变量stats
[h,p,varci,stats]=vartest(x,var0,alpha,tail)
```

&emsp;&emsp;总体均值未知时的单个正态总体方差的比较 $F$ 检验,可用 **vartest2 函数** 完成 <br><br>
<center>$H_0:\sigma^2_1=\sigma^2_2\quad H_1:\sigma^2_1\ne\sigma^2_2$</center>

``` matlab
%第一组样本观测值向量
x=[20.1  20 19.3 20.6 20.2 19.9 20 19.9 19.1 19.9];

%第二组样本观测值向量
y=[18.6 19.1 20 20 20 19.7 19.9 19.6 20.2];

alpha=0.05; %显著性水平为0.05
tail='both'; %尾部类型为双侧

%调用vartest2函数作两个正态总体方差比较检验
%返回变量h，检验的p值，方差之比的置信区间varci，结构体变量stats
[h,p,varci,stats]=vartest2(x,y,alpha,tail)
```

### 3.2 分布的检验

&emsp;&emsp;Matlab 统计工具箱中提供了 chi2gof、jbtest、ktest、kstest2 和 lillietest 函数，用来进行分布的检验，但缺点是拟合优度检验对分组结果比较敏感

- **chi2gof 函数** 用来作分布的卡方拟合优度检验，检验样本是否服从制定的分布

``` matlab
score=xlsread('example02_14.xls','Sheet1','G2:G52');

%去掉总成绩中的0，即缺考成绩
score=score(score>0);

%进行卡方拟合优度检验
[h,p,stats]=chi2gof(score)
```

- **jbtest 函数** 用来作 Jarque-Bera 检验，检验样本是否服从正态分布，调用该函数时不需要指定分布的均值和方差，只是基于样本偏度和峰度进行正态性检验，结果受异常值的影响比较大，可能会出现比较大的偏差

``` matlab
randn('seed',0)  %指定随机数生成器的初始种子为0
x=randn(10000,1);%生成10000个服从标准正态分布的随机数
h=jbtest(x)   %调用jbtest函数进行正态性检验

h = 0
x(end)=5; %将向量的最后一个元素改为5
h=jbtest(x) 
h= 1
```

- **kstest 函数** 用来作单个样本的 Kolmogorov-Smirnov 检验，其比较一个频率分布 $f(x)$ 与理论分布 $g(x)$ 或者两个观测值分布的检验方法，原假设 $H_0$ 两个数据分布一致或者数据符合理论分布 $D=\max|f(x)- g(x)|$，当实际观测值 $D>D(n,a)$ 则拒绝 $H_0$，否则则接受 $H_0$ 假设 <br>

  **kstest2 函数** 用来作两个样本的 Kolmogorov-Smirnov 检验，它可以做双侧检验，检验两个样本是否服从相同的分布，也可以做单侧检验，检验一个样本的分布函数是否在另一个样本的分布函数之上或之下，这里的分布是完全确定的，不含有未知参数


``` matlab
h=kstest2(x1,x2)
h=kstest2(x1,x2,alpha)

F1=cdfplot(data1);
set(F1,'Color','r');
hold on
F2=cdfplot(data2);
set(F2,'Color','k');
%可看出两组经验分布函数的相似程度
```

![kstest](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/kstest.png)

> 除此之外还可以造一个随机数组成的带有目标均值和标准差的正态分布，将现有样本与随机正态分布进行比较

``` matlab 
randn('seed',0) %指定随机数生成器的初始种子为0
%产生10000个服从均值为79，标准差为10的正态分布的随机数，构成一个列向量x
x=normrnd(79,10,10000,1);
%调用kstest2函数检验总成绩数据与随机数向量x是否服从相同的分布
[h,p]=kstest2(score,x,0.05)
```

- **ksdensity 函数** 用来求核密度估计，其中窗宽的取值会影响到 $f(x)$ 的光滑程度，如果 $h$ 取较大的值，距 $x$ 较近的点与较远的点所对应的核函数值差距不大，此时 $f(x)$ 的图像是较为光滑的曲线，但同时也丢失了数据所包含的一些信息；如果 $h$ 取较小的值，$f(x)$ 的图像是不光滑的折线，但它能反映出每个数据所包含的信息

``` matlab
%调用ecdf函数计算xc处的经验分布函数值f_ecdf
[f_ecdf,xc]=ecdf(score);
%新建图形窗口，然后绘制频率直方图，对应7个小区间
figure;
ecdfhist(f_ecdf,xc,7);
hold on;
xlabel('考试成绩');
ylabel('f(x)');

%调用ksdensity函数进行核密度估计
[f_ks1,xi1,u1]=ksdensity(score);
plot(xi1,f_ks1,'k','linewidth',3)
%计算xi1处的正态分布密度函数值，正态分布的均值为55，标准差为10
f_norm=normpdf(xi1,55,10);
%绘制正态分布密度函数图，并设置线条为红色点划线，线宽为3
plot(xi1,f_norm,'r-.','linewidth',3)
legend('频率直方图','核密度估计图','正态分布密度图','Location','NorthWest')
u1 %查看窗宽
```

![ksdensity](%E7%AC%AC11%E7%AB%A0_%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1%E4%B8%AD%E4%BD%BF%E7%94%A8Matlab%E8%BD%AF%E4%BB%B6.assets/ksdensity.png)

---

## 第04节 Matlab 方差分析

### 4.1 单因素一元方差分析

- **正态性假设**

``` matlab
clc;clear;close all;
[num,txt,raw] = xlsread('Resting State.xlsx');

%% one-way ANOVA
x=num(:,1);
group=num(:,4);

%正态性检验
for i=1:3
    x_i=x(group==i); %提取第i个group的睁眼状态下的脑电信号功率值
    [h,p]=lillietest(x_i); %正态性检验
    result(i,:)=p; 
end

result %检验正态检验的p值
result =
    0.5000
    0.5000
    0.5000
```

- **方差齐次性检测**

``` matlab
%方差齐性检验
[p,stats]=vartestn(x,group); %调用vartestn函数进行方差齐次性检验
```

- **方差分析**

``` matlab
%方差分析
[p,tbl,stats] = anova1(x,group);%单因素一元方差分析
```

- **多重比较**

``` matlab
%多重比较
[c,m,h,gnames]=multcompare(stats); %多重比较
```

&emsp;&emsp;**multcompare 函数** 还生成一个交互式图形，可以通过鼠标单击的方式进行两两比较检验，该交互式图形上用一个符号（圆圈）标出了每一组的组均值，用一条之间段标出了每个组的组均值的置信区间，如果某两条线段不相交，即没有重叠的部分则说明这两个组的组均值之间的差异是显著的 
&emsp;&emsp;如果某两条直线段有重叠部分，则说明这两个组的组均值之间的差异是不显著的，可以用鼠标在图上任意选一个组，选中的组以及与选中的组差异显著的其他组均用高亮显示，选中的组用蓝色显示，与选中的组差异显著的其他组用红色显示

### 4.2 双因素一元方差分析

&emsp;&emsp;为了研究肥料使用量对水稻产量的影响，某研究所做了氮、磷两种肥料施用量的二因素试验，氮肥用量设低、中、高三个水平，分布使用 $N_1$，$N_2$ 和 $N_3$ 表示；磷肥用量设低、高2个水平，分别用 $P_1$，$P_2$ 表示，共 $3x2=6$ 个处理，重复 $4$ 次，随机区组设计测得水稻产量如下表

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=5>
 <tr height=18>
  <td rowspan=2 style='text-align: center;'><strong>处理</strong></td>
  <td colspan=4 style='text-align: center;'><strong>区间</strong></td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'>$1$</td>
  <td style='text-align: center;'>$2$</td>
  <td style='text-align: center;'>$3$</td>
  <td style='text-align: center;'>$4$</td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'>$N_1P_1$</td>
  <td style='text-align: center;'>$38$</td>
  <td style='text-align: center;'>$29$</td>
  <td style='text-align: center;'>$36$</td>
  <td style='text-align: center;'>$40$</td>
 </tr>
  <tr height=18>
  <td style='text-align: center;'>$N_1P_2$</td>
  <td style='text-align: center;'>$45$</td>
  <td style='text-align: center;'>$42$</td>
  <td style='text-align: center;'>$37$</td>
  <td style='text-align: center;'>$43$</td>
 </tr>
  <tr height=18>
  <td style='text-align: center;'>$N_2P_1$</td>
  <td style='text-align: center;'>$58$</td>
  <td style='text-align: center;'>$46$</td>
  <td style='text-align: center;'>$52$</td>
  <td style='text-align: center;'>$51$</td>
 </tr>
  <tr height=18>
  <td style='text-align: center;'>$N_2P_2$</td>
  <td style='text-align: center;'>$67$</td>
  <td style='text-align: center;'>$70$</td>
  <td style='text-align: center;'>$65$</td>
  <td style='text-align: center;'>$71$</td>
 </tr>
  <tr height=18>
  <td style='text-align: center;'>$N_3P_1$</td>
  <td style='text-align: center;'>$62$</td>
  <td style='text-align: center;'>$64$</td>
  <td style='text-align: center;'>$61$</td>
  <td style='text-align: center;'>$70$</td>
 </tr>
  <tr height=18>
  <td style='text-align: center;'>$N_3P_2$</td>
  <td style='text-align: center;'>$58$</td>
  <td style='text-align: center;'>$63$</td>
  <td style='text-align: center;'>$71$</td>
  <td style='text-align: center;'>$69$</td>
 </tr>
</table>

&emsp;&emsp;根据上表中的数据，不考虑区组因素，分析氮、磷两种肥料的施用量对水稻产量是否有显著性影响，并分析交互作用是否显著。取显著性水平 $a=0.05$

- **方差分析**

``` matlab
% 定义一个矩阵，输入原始数据
yield=[38 29 36 40
    45 42 37 43
    58 46 52 51
    67 70 65 71
    62 64 61 70
    58 63 71 69];
yield=yield';  %矩阵转置
% 将数据矩阵yield转换成8行3列的矩阵，列对应因素A（氮），行对应因素B（磷）
yield=[yield(:,[1,3,5]);yield(:,[2,4,6])];
 
% 定义元胞数组，以元胞数组形式显示转换后的数据
top={'因素','N1','N2','N3'};
left={'P1';'P1';'P1';'P1';'P2';'P2';'P2';'P2'};
 
% 显示数据
[top;left,num2cell(yield)];
 
% reps表示因素A和B下的每一个水平组合下重复实验的次数
reps=4;
 
% 调用anova2函数作双因素方差分析，返回检验的p值向量，方差分析表，结构体标量stats
[p,table,stats]=anova2(yield,reps)
```

&emsp;&emsp;因素 $A$、因素 $B$ 以及他们的交互作用对应的检验 $p$ 值均小于给定的显著性水平 $0.05$，所以可以认为氮、磷两种肥料的施用量对水稻的产量均有显著性影响，并且他们之间的交互作用也是非常显著的，可以作进一步分析例如进行多重分析，找出因素 $A$ 与 $B$ 在哪种水平的组合下水稻的平均产量最高

- **多重比较**

``` matlab
%对列（因素A）进行多重比较
[c_A,m_A,h,gnames]=multcompare(stats,'estimate','column');
head={'组序号','组序号','置信下限','置信上限','组均值差','p-value'};
[head;num2cell(c_A)]  %将矩阵c转为元胞数组，并与head一起显示
head={'组序号','均值的估计值','标准误差'};
[head;cellstr(gnames),num2cell(m_A)]  %将m转为元胞数组，和gnames一起显示
  
ans =
  4×6 cell 数组
    {'组序号'}    {'组序号'}    {'置信下限' }    {'置信上限' }    {'组均值差' }    {'p-value'   }
    {[    1]}    {[    2]}    {[-26.8971]}    {[-21.2500]}    {[-15.6029]}    {[4.9194e-08]}
    {[    1]}    {[    3]}    {[-31.6471]}    {[     -26]}    {[-20.3529]}    {[3.1051e-09]}
    {[    2]}    {[    3]}    {[-10.3971]}    {[ -4.7500]}    {[  0.8971]}    {[    0.1084]}
 
ans =
  4×3 cell 数组
    {'组序号'}    {'均值的估计值'}    {'标准误差'}
    {'1'    }    {[   38.7500]}    {[ 1.5646]}
    {'2'    }    {[        60]}    {[ 1.5646]}
    {'3'    }    {[   64.7500]}    {[ 1.5646]}
 
```

```
%对行（因素B）进行多重比较
[c_B,m_B,h,gnames]=multcompare(stats,'estimate','row')
head={'组序号','组序号','置信下限','置信上限','组均值差','p-value'};
[head;num2cell(c_B)]  %将矩阵c转为元胞数组，并与head一起显示
head={'组序号','均值的估计值','标准误差'};
[head;cellstr(gnames) num2cell(m_B)]  %将m转为元胞数组，和gnames一起显示
 
ans =
  2×6 cell 数组
    {'组序号'}    {'组序号'}    {'置信下限' }    {'置信上限'}    {'组均值差'}    {'p-value'   }
    {[    1]}    {[    2]}    {[-11.6289]}    {[-7.8333]}    {[-4.0378]}    {[3.9813e-04]}
 
ans =
  3×3 cell 数组
    {'组序号'}    {'均值的估计值'}    {'标准误差'}
    {'1'    }    {[   50.5833]}    {[ 1.2775]}
    {'2'    }    {[   58.4167]}    {[ 1.2775]}
```

### 4.3 多因素一元方差分析

&emsp;&emsp;根据上表中的数据，分析氮、磷哪种组合对水稻产量是否有显著性影响，取显著性水平 $a=0.05$

- **方差分析**

``` matlab
% 定义一个矩阵，输入原始数据
yield=[38 29 36 40
    45 42 37 43
    58 46 52 51
    67 70 65 71
    62 64 61 70
    58 63 71 69];
yield=yield'  % 矩阵转置

% 将数据矩阵yield按列拉长成24行1列的向量
yield=yield(:);

% 定义因素A(氮)的水平列表向量
A=strcat({'N'},num2str([ones(8,1);2*ones(8,1);3*ones(8,1)]));
 
% 定义因素B(磷)的水平列表向量
B=strcat({'P'},num2str([ones(4,1);2*ones(4,1)]));
B=[B;B;B];
 
% 将因素A、B的水平列表向量与yield向量放在一起构成一个元胞数组，以元胞数组形式显示出来
[A,B,num2cell(yield)]
 
% 指定因素名称，A表示氮肥施用量，B表示磷肥施用量
varnames={'A','B'};
 
% 调用anovan函数作双因素一元方差分析，返回主效应A、B和交互效应AB所对应的p值向量
% 还返回方差分析表table，结构体变量stats，标识模型效应项的矩阵term
[p,table,stats,term]=anovan(yield,{A,B},'model','full','varnames',varnames)
```

- **多重比较**

``` matlab
%多重比较
[c,m,h,gnames]=multcompare(stats,'dimension',[1 2])
 
%查看各处理的均值
[gnames,num2cell(m)]
 
```

```
ans =
  16×6 cell 数组
    {'组序号'}    {'组序号'}    {'置信下限' }    {'置信上限' }    {'组均值差' }    {'p-value'   }
    {[    1]}    {[    2]}    {[-25.9446]}    {[-16.0000]}    {[ -6.0554]}    {[8.7776e-04]}
    {[    1]}    {[    3]}    {[-38.4446]}    {[-28.5000]}    {[-18.5554]}    {[5.1236e-07]}
    {[    1]}    {[    4]}    {[-15.9446]}    {[      -6]}    {[  3.9446]}    {[    0.4236]}
    {[    1]}    {[    5]}    {[-42.4446]}    {[-32.5000]}    {[-22.5554]}    {[8.7653e-08]}
    {[    1]}    {[    6]}    {[-39.4446]}    {[-29.5000]}    {[-19.5554]}    {[3.1431e-07]}
    {[    2]}    {[    3]}    {[-22.4446]}    {[-12.5000]}    {[ -2.5554]}    {[    0.0093]}
    {[    2]}    {[    4]}    {[  0.0554]}    {[ 10.0000]}    {[ 19.9446]}    {[    0.0483]}
    {[    2]}    {[    5]}    {[-26.4446]}    {[-16.5000]}    {[ -6.5554]}    {[6.2868e-04]}
    {[    2]}    {[    6]}    {[-23.4446]}    {[-13.5000]}    {[ -3.5554]}    {[    0.0047]}
    {[    3]}    {[    4]}    {[ 12.5554]}    {[ 22.5000]}    {[ 32.4446]}    {[1.4062e-05]}
    {[    3]}    {[    5]}    {[-13.9446]}    {[ -4.0000]}    {[  5.9446]}    {[    0.7926]}
    {[    3]}    {[    6]}    {[-10.9446]}    {[      -1]}    {[  8.9446]}    {[    0.9995]}
    {[    4]}    {[    5]}    {[-36.4446]}    {[-26.5000]}    {[-16.5554]}    {[1.4498e-06]}
    {[    4]}    {[    6]}    {[-33.4446]}    {[-23.5000]}    {[-13.5554]}    {[7.8003e-06]}
    {[    5]}    {[    6]}    {[ -6.9446]}    {[  3.0000]}    {[ 12.9446]}    {[    0.9251]}
 
ans =
  7×3 cell 数组
    {'组序号'    }    {'均值的估计值'}    {'标准误差'}
    {'A=N1,B=P1'}    {[   35.7500]}    {[ 2.2127]}
    {'A=N2,B=P1'}    {[   51.7500]}    {[ 2.2127]}
    {'A=N3,B=P1'}    {[   64.2500]}    {[ 2.2127]}
    {'A=N1,B=P2'}    {[   41.7500]}    {[ 2.2127]}
    {'A=N2,B=P2'}    {[   68.2500]}    {[ 2.2127]}
    {'A=N3,B=P2'}    {[   65.2500]}    {[ 2.2127]}
```

&emsp;&emsp;返回的矩阵 $c$ 是 $6$ 种处理 $(N_1P_1,N_2P_1,N_3P_1,N_1P_2,N_2P_2,N_3P_2)$ 间多重比较的结果矩阵
- 每一行的前 $2$ 列是进行比较的两个处理的编号
- 第 $3$ 列是两个处理均值差的 $95\%$ 置信下限
- 第 $4$ 列是两个处理的均值之差
- 第 $5$ 列是两个处理均值差的 $95\%$ 置信下限

> 当两个处理均值差的 $95\%$ 置信区间不包含 $0$ 时，说明在显著性水平 $0.05$ 下，这两个处理均值间差异是显著的

&emsp;&emsp;$m$ 矩阵列出了 $64$ 种处理的平均值，第 $5$ 个处理 $N_2P_2$ 的平均值最大，由矩阵 $c$ 或交互式多重比较的图中可以得到，处理 $5$ 与处理 $3,6$ 差异不显著，所以可以认为第 $3$ 个和第 $6$ 个处理也是可以的，所以综上可以在处理 $3,5,6$ 中做出选择，即 $N_3P_1,N_2P_2,N_3P_2$
