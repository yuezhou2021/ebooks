# 第10章 bootstrap 方法

---

## 序言

### 1.内容介绍

&emsp;&emsp;本章详细介绍了非参数 bootstrap 方法、参数 bootstrap 方法等定义，并对其原理与例题进行了一一阐述

### 2.理论目标

- 掌握估计量的标准误差的 bootstrap 估计
- 掌握估计量的均方误差及偏差的 bootstrap 估计
- 掌握参数与非参数 bootstrap 方法
- 掌握 bootstrap 置信区间
- 掌握 bootstrap-t 法
- 掌握 bootstrap 假设检验的一般形式

### 3.实践目标

- 无

### 4.实践案例

- 无

### 5.内容目录

- 1.非参数 bootstrap 方法
- 2.参数 bootstrap 方法
- 3.bootstrap 假设检验方法举例

---

## 第01节 非参数 bootstrap 方法

&emsp;&emsp;设总体的分布 $F$ 未知，但已经有一个容量为 $n$ 的来自分布 $F$ 的数据样本
- 自这一样本按 **放回抽样** 的方法抽取一个容量为 $n$ 的样本，这种样本称为 **bootstrap 样本** 或 **自助样本**
- 相继地、独立地自原始样本中取很多个 bootstrap 样本，利用这些样本对总体 $F$ 进行统计推断，这种方法称为 **非参数 bootstrap 方法** 或 **自助法**

> 这一方法可以用于当对总体知之甚少的情况，它是近代统计中的一种用于数据处理的重要实用方法，其实现需要在计算机上作大量的计算，随着计算机威力的增长，它已成为一种流行的方法

### 1.1 估计量的标准误差的 bootstrap 估计

&emsp;&emsp;在估计总体未知参数 $\theta$ 时，不但要给出 $\theta$ 的估计 $\hat{\theta}$ 还需指出这一估计 $\hat{\theta}$ 的精度，通常用估计量 $\hat{\theta}$ 的 **标准差** $\sqrt{D(\hat{\theta})}$ 来度量估计的精度

> 估计置 $\hat{\theta}$ 的标准差 $\sigma_{\hat{\theta}}=\sqrt{D(\hat{\theta})}$ 也称为估计量 $\hat{\theta}$ 的 **标准误差**

&emsp;&emsp;在应用中 $\hat{\theta}$ 的抽样分布往往是很难处理的，因此 $\sqrt{D(\hat{\theta})}$ 常没有一个简单的表达式，不过可以用 **计算机模拟** 的方法来求得 $\sqrt{D(\hat{\theta})}$ 的估计，为此 $F$ 产生很多容量为 $n$ 的样本 (设为 $B$ 个)，对于每一个样本计算 $\hat{\theta}$ 的值可得 $\hat{\theta}_1,\hat{\theta}_2,\dots,\hat{\theta}_B$，则 $\sqrt{D(\hat{\theta})}$ 可以用 <br><br>
<center>$\hat{\sigma}_{\hat{\theta}}=\sqrt{\dfrac{1}{B-1}\sum\limits^{B}_{i=1}(\hat{\theta}_i-\bar{\theta})^2}$</center>

来估计，其中 $\bar{\theta}=\dfrac{1}{B}\sum\limits^{B}_{i=1}\hat{\theta}_i$，然而 $F$ 常常是未知的，这样就无法产生模拟样本，因此现设分布 $F$ 未知，$x_1,x_2,\dots,x_n$ 是来自 $F$ 的样本值，$F_n$ 是相应的经验分布函数，在第六章 `抽样与抽样分布` 中证明当 $n$ 很大时 $F_n$ 接近 $F$，即可以用 $F_n$ 代替原式中的 $F$，则 $\hat{\theta}$ 的标准误差 $\sqrt{D(\hat{\theta})}$ 可以用 <br><br>
<center>$\hat{\sigma}_{\hat{\theta}}=\sqrt{\dfrac{1}{B-1}\sum\limits^{B}_{i=1}(\hat{\theta}^*_i-\bar{\theta}^*)^2}$</center>

来估计，其中 $\bar{\theta}^*=\dfrac{1}{B}\sum\limits^{B}_{i=1}\hat{\theta}^*_i$，上式即为 $\sqrt{D(\hat{\theta})}$ 的 bootstrap 估计

&emsp;&emsp;综上所述得到求 $\sqrt{D(\hat{\theta})}$ 的 bootstrap 估计的步骤为
- **bootstrap 样本**：自原始数据样本 $x=(x_1,x_2,\dots,x_n)$ 按放回抽样的方法抽得容量为 $n$ 的样本 $x^*=(x^*_1,x^*_2,\dots,x^*_n)$ 
- **bootstrap 估计**：相继地、独立地求出 $B$ 个容量为 $n$ 的 bootstrap 样本，$x^{*_i}=(x^{*_i}_1,x^{*_i}_2,\dots,x^{*_i}_n)$，$i=1,2,\dots,B$，对于第 $i$ 个 bootstrap 样本计算 $\hat{\theta}^*_i=\hat{\theta}(x^{*_i}_1,x^{*_i}_2,\dots,x^{*_i}_n)$ 
- **bootstrap 标准误差**：$\hat{\sigma}_{\hat{\theta}}=\sqrt{\dfrac{1}{B-1}\sum\limits^{B}_{i=1}(\hat{\theta}^*_i-\bar{\theta}^*)^2}$

### 1.2 估计量的均方误差及偏差的 bootstrap 估计

&emsp;&emsp;设 $X=(X_1,X_2,\dots,X_n)$ 是来自总体 $F$ 的样本且 $F$ 未知，$R=R(X)$ 是感兴趣的随机变量依赖于样本 $X$，假设希望去估计 $R$ 的分布的某些特征，就可以按照 bootstrap 的三个步骤进行估计，但在 **bootstrap 估计** 步骤中对于第 $i$ 个 bootstrap 样本 $x^{*_i}=(x^{*_i}_1,x^{*_i}_2,\dots,x^{*_i}_n)$ 计算 <br><br>
<center>$R^*_i=R(x^*_i)$ 代替计算 $\theta^*_i$</center>

#### 1.2.1 均方误差估计

&emsp;&emsp;**例1**：设金属元素铂的升华热是具有分布函数 $F$ 的连续型随机变量，$F$ 的中位数 $\theta$ 是未知参数，现测得以下的数据 (单位 $kcal/mol$)，以样本中位数 $M=M(X)$ 作为总体中位数 $\theta$ 的估计，试求均方误差 $\mathrm{MSE}=E[(M-\theta)^2]$ 的 bootstrap 估计

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=13>
 <tr height=18>
  <td style='text-align: center;'>$136.3$</td>
  <td style='text-align: center;'>$136.6$</td>
  <td style='text-align: center;'>$135.8$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$134.7$</td>
  <td style='text-align: center;'>$135.0$</td>
  <td style='text-align: center;'>$134.1$</td>
  <td style='text-align: center;'>$143.3$</td>
  <td style='text-align: center;'>$147.8$</td>
  <td style='text-align: center;'>$148.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$135.2$</td>
  <td style='text-align: center;'>$134.9$</td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'>$149.5$</td>
  <td style='text-align: center;'>$141.2$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$135.8$</td>
  <td style='text-align: center;'>$135.0$</td>
  <td style='text-align: center;'>$133.7$</td>
  <td style='text-align: center;'>$134.4$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.5$</td>
  <td style='text-align: center;'>$134.3$</td>
  <td style='text-align: center;'>$135.2$</td>
 </tr>
</table>

&emsp;&emsp;将原始样本自小到大排序，左起第 $13$ 个数为 $135.0$，左起第 $14$ 个数为 $135.2$，于是样本中位数为 $(135.0+135.2)=135.1$，以 $135.1$ 作为总体中位数 $\theta$ 的估计，即 $\hat{\theta}=135.1$，取 $R=R(X)=(M-\hat{\theta})^2$，需估计 $R(X)$ 的均值 $E[(M-\hat{\theta})^2]$，相继地、独立地抽取 $10000$ 个 bootstrap 样本

- 样本 $1$ 的样本中位数为 $135.3$

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=13>
 <tr height=18>
  <td style='text-align: center;'>$133.2$</td>
  <td style='text-align: center;'>$134.1$</td>
  <td style='text-align: center;'>$134.1$</td>
  <td style='text-align: center;'>$134.1$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$135.0$</td>
  <td style='text-align: center;'>$135.2$</td>
  <td style='text-align: center;'>$135.4$</td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.8$</td>
  <td style='text-align: center;'>$135.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$136.3$</td>
  <td style='text-align: center;'>$136.3$</td>
  <td style='text-align: center;'>$136.6$</td>
  <td style='text-align: center;'>$136.6$</td>
  <td style='text-align: center;'>$141.2$</td>
  <td style='text-align: center;'>$143.3$</td>
  <td style='text-align: center;'>$143.3$</td>
  <td style='text-align: center;'>$147.8$</td>
  <td style='text-align: center;'>$148.8$</td>
 </tr>
</table>

<center>$\vdots$</center>

- 样本 $10000$ 的样本中位数为 $134.9$

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=13>
 <tr height=18>
  <td style='text-align: center;'>$134.3$</td>
  <td style='text-align: center;'>$134.5$</td>
  <td style='text-align: center;'>$134.5$</td>
  <td style='text-align: center;'>$134.5$</td>
  <td style='text-align: center;'>$134.7$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.8$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$134.9$</td>
 </tr>
 <tr height=18>
  <td style='text-align: center;'>$134.9$</td>
  <td style='text-align: center;'>$135.0$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.4$</td>
  <td style='text-align: center;'>$135.8$</td>
  <td style='text-align: center;'>$136.6$</td>
  <td style='text-align: center;'>$146.5$</td>
  <td style='text-align: center;'>$146.5$</td>
  <td style='text-align: center;'>$147.8$</td>
  <td style='text-align: center;'>$148.8$</td>
 </tr>
</table>

&emsp;&emsp;对于用第 $i$ 个样本计算 $R^*_i=R(x^{*_i})=(M^*_i-\hat{\theta})^2=(M^*_i-135.1)^2$，即对样本 $1$ 有 $(M^*_1-135.1)^2=(135.3-135.1)^2=0.04$，对样本 $10000$ 有 $(M^*_{10000}-135.1)^2=(134.9-135.1)^2=0.04$，用这 $10000$ 个数的平均值 <br><br>
<center>$\dfrac{1}{10000}\sum\limits^{10000}_{i=1}(M^*_i-135.1)^2=0.07$</center><br>
近似 $E[(M-\hat{\theta})^2]$，即得 $\mathrm{MSE}[(M-\theta)^2]$ 的 bootstrap 估计为 $0.07$

#### 1.2.2 偏差估计

&emsp;&emsp;设 $X=(X_1,X_2,\dots,X_n)$ 是来自总体 $F$ 的样本，$\hat{\theta}=\hat{\theta}(X_1,X_2,\dots,X_n)$ 是参数 $\theta$ 的估计量，$\theta$ 的估计 $\hat{\theta}$ 关于 $\theta$ 的偏差定义为 <br><br>
<center>$b=E(\hat{\theta}-\theta)=E(\hat{\theta}-\theta)$</center>

当 $\hat{\theta}$ 是 $\theta$ 的无偏估计时 $b=0$，在 **例1** 中以样本中位数 $M=M(X)$ 作为总体中位数 $\theta$ 的估计，试求偏差 $b=E(M-\theta)$ 的 bootstrap 估计

&emsp;&emsp;上述可知原始样本中位数 $135.1$ 作为总体中位数 $\theta$ 的估计，即 $\hat{\theta}=135.1$，取 $R=R(X)=M-\hat{\theta}$，需估计 $R(X)$ 的均值 $E(M-\hat{\theta})$，对于第 $i$ 个样本计算 $R^*_i=R(x^{*_i})=(M^*_i-\hat{\theta})=M^*_i-135.1$，即对样本 $1$ 有 $M^*_1-135.1=135.3-135.1=0.2$，对样本 $10000$ 有 $M^*_{10000}-135.1=134.9-135.1=-0.2$，将 $10000$ 个数取平均值得到偏差 $b$ 的 bootstrap 估计<br><br>
<center>$b^*=\dfrac{1}{10000}\sum\limits^{10000}_{i=1}M^*_i-135.1=0.26$</center><br>

### 1.3 bootstrap 置信区间

&emsp;&emsp;设 $X=(X_1,X_2,\dots,X_n)$ 是来自总体 $F$ 容量为 $n$ 的样本，$x=(x_1,x_2,\dots,x_n)$ 是一个已知的样本值，$\hat{\theta}=\hat{\theta}(X_1,X_2,\dots,X_n)$ 是未知参数 $\theta$ 的估计量，需要求得 $\theta$ 的置信水平为 $1-a$ 的置信区间

&emsp;&emsp;相继地、独立地从样本 $x=(x_1,x_2,\dots,x_n)$ 中抽出 $B$ 个容量为 $n$ 的 bootstrap 样本，对于每个 bootstrap 样本求出 $\theta$ 的 bootstrap 估计 $\hat{\theta}^*_1,\hat{\theta}^*_2,\dots,\hat{\theta}^*_B$ 将它们自小到大排序可得 <br><br>
<center>$\hat{\theta}^*_1\le\hat{\theta}^*_2\le\dots\le\hat{\theta}^*_B$</center><br>
取 $R(X)=\hat{\theta}$ 用对应的的分布 $R(X^*)=\hat{\theta}^*$ 作为 $R(X)$ 的分布的近似，求出 $R(X^*)$ 的分布的近似分位数 $\hat{\theta}^*_{\tfrac{a}{2}}$ 和 $\hat{\theta}^*_{1-\tfrac{a}{2}}$ 使 <br><br>
<center>$P(\hat{\theta}^*_{\tfrac{a}{2}}<\hat{\theta}^*<\hat{\theta}^*_{1-\tfrac{a}{2}})=1-a\quad\rightarrow\quad P(\hat{\theta}^*_{\tfrac{a}{2}}<\theta<\hat{\theta}^*_{1-\tfrac{a}{2}})=1-a$</center>

&emsp;&emsp;记 $k_1=\big[B\times\dfrac{a}{2}\big]$，$k_2=\big[B\times\big(1-\dfrac{a}{2}\big)\big]$，上式中分别以 $\hat{\theta}^*_{k_1}$  和 $\hat{\theta}^*_{k_2}$ 作为分位数 $\hat{\theta}^*_{\tfrac{a}{2}}$，$\hat{\theta}^*_{1-\tfrac{a}{2}}$ 的估计，得到近似等式 <br><br>
<center>$P(\hat{\theta}^*_{k_1}<\theta<\hat{\theta}^*_{k_2})=1-a$</center>

于是由上式就得到 $\theta$ 的置信水平为 $l-a$ 的近似置信区间 $(\hat{\theta}^*_{k_1},\hat{\theta}^*_{k_2})$，这一区间称为 $\theta$ 的置信水平为 $1-a$ 的 **bootstrap 置信区间**，这种求置信区间的方法称为 **分位数法**

&emsp;&emsp;**例1** 中
- 以样本中位数作为总体中位数 $\theta$ 的估计求 $\theta$ 的置信水平为 $0.95$ 的 bootstrap 置信区间

&emsp;&emsp;对于每一个 bootstrap 样本算出中位数 $M^*_1,M^*_2,\dots,M^*_{10000}$，将它们自小到大排序得到 $M^*_1\le M^*_2\le\dots\le M^*_{10000}$，由 $B=10000$，$1-a=0.95$，$a=0.05$，$k_1=\big[10000\times\dfrac{0.05}{2}\big]=250$，$k_2=\big[10000\times(1- \dfrac{0.05}{2})\big]=9750$，可得 bootstrap 置信区间为 <br><br>
<center>$(M^*_{250},M^*_{9750})=(134.8,135.8)$</center>

- 以样本 $20\%$ 截尾均值作为总体 $20\%$ 截尾均值 $\mu_t$ 的估计，求 $\mu_t$ 的置信水平为 $0.95$ 的 bootstrap 置信区间

&emsp;&emsp;对于每一个 bootstrap 样本算出样本 $20\%$ 截尾均值 $\bar{x}^*_{t_1},\bar{x}^*_{t_2},\dots,\bar{x}^*_{t_{10000}}\;\;$ 将它们自小到大排序得到 $\bar{x}^*_{t_1}\le\bar{x}^*_{t_2}\le\dots\le\bar{x}^*_{t_{10000}}\;\;$ 按分位法可得 $20\%$ 截尾均值bootstrap 的置信水平为 $0.95$ 的置信区间为 <br><br>
<center>$(\bar{x}^*_{t_{250}}\;,\bar{x}^*_{t_{9750}}\;)=(134.85,136.92)$</center>

### 1.4 bootstrap-t 法

&emsp;&emsp;设 $X=(X_1,X_2,\dots,X_n)$ 是来自总体 $F$ 容量为 $n$ 的样本，$x=(x_1,x_2,\dots,x_n)$ 是一个已知的样本值，均值 $\mu$ 和方差 $\sigma^2$ 均为未知参数，需要利用样本值 $x$ 来估计 $\mu$

> 第七章 `参数估计` 中提到假设总体 $F$ 具有正态分布，函数 $t=\dfrac{\bar{X}-\mu}{S/\sqrt{n}}$ 的分布与 $\mu$ 无关，它是一
个枢轴量而且有 $t\backsim t(n-1)$，利用枢轴量 $t$ 就能求得 $\mu$ 的置信区间，但现在总体 $F$ 不具有正态分布，但可证 $t$ 仍是一个枢轴量，然而 $t$ 的分布就不是 $t(n-1)$ 分布，这样就不能按第七章的方法求得 $\mu$ 的置信区间了

&emsp;&emsp;以原始样本 $x=(x_1,x_2,\dots,x_n)$ 的样本均值 $\bar{x}=\dfrac{1}{n}\sum\limits^{n}_{i=1}x_i$ 作为 $\mu$ 的估计，考虑与 $t$ 相应的枢轴量 $W^*=\dfrac{\bar{X}^*-\bar{x}}{S^*/\sqrt{n}}$，此处 $\bar{X}^*$，$S^*$ 分别为与 $\bar{X}$，$S$ 相应的 bootstrap 样本均值与样本标准差，用 $W^*$ 的分布近似 $t$ 的分布，求出 $W^*$ 的近似分位数 $w^*_{\tfrac{a}{2}}$，$w^*_{1-\tfrac{a}{2}}$ 使 <br><br>
<center>$P\big(w^*_{\tfrac{a}{2}}<\dfrac{\bar{X}^*-\bar{x}}{S^*/\sqrt{n}}<w^*_{1-\tfrac{a}{2}}\big)=1-a$</center>

&emsp;&emsp;于是近似地有 $P\big(w^*_{\tfrac{a}{2}}<\dfrac{\bar{X}-\mu}{S/\sqrt{n}}<w^*_{1-\tfrac{a}{2}}\big)=1-a$ 或 $P\big(\bar{X}-w^*_{1-\tfrac{a}{2}}\dfrac{S}{\sqrt{n}}<\mu<\bar{X}-w^*_{\tfrac{a}{2}}\dfrac{S}{\sqrt{n}}\big)=1-a$，将 $W^*$ 的 $B$ 个 bootstrap 值自小到大排序，记 $k_1=\big[B\times\dfrac{a}{2}\big]$，$k_2=\big[B\times\big(1-\dfrac{a}{2}\big)\big]$，上式中分别以 $w^*_{k_1}$  和 $w^*_{k_2}$ 作为分位数 $w^*_{\tfrac{a}{2}}$，$w^*_{1-\tfrac{a}{2}}$ 的估计，得到近似等式 <br><br>
<center>$P\big(\bar{X}-w^*_{k_2}\dfrac{S}{\sqrt{n}}<\mu<\bar{X}-w^*_{k_1}\dfrac{S}{\sqrt{n}}\big)=1-a$</center>

由上式得到 $\mu$ 的置信水平为 $1-a$ 的 bootstrap 置信区间 $(\bar{X}-w^*_{k_2}\dfrac{S}{\sqrt{n}},\bar{X}-w^*_{k_1}\dfrac{S}{\sqrt{n}}$，这一方法称为 **bootstrap-t 法**

> 用非参数 bootstrap 法来求参数的近似置信区间的优点是不需要假设所研究的总体的分布函数 $F$ 的形式，bootstrap 样本是来自 **已知的数据** (原始样本) 而且可以适用于小样本，且能用于各种统计量 (不限于样本均值)

---

## 第02节 参数 bootstrap 方法

### 2.1 参数 bootstrap

&emsp;&emsp;假设所研究的总体的分布函数 $F(x;\beta)$ 的形式已知，但其中包含未知参数 $\beta$，现在已知有一个来自 $F(x;\beta)$ 的样本 $X_1,X_2,\dots,X_n$，利用这一样本求出 $\beta$ 的最大似然估计 $\hat{\beta}$，在 $F(x;\beta)$ 中以 $\hat{\beta}$ 替代 $\beta$ 得到 $F(x;\hat{\beta})$，接着在 $F(x;\hat{\beta})$ 中产生容量为 $n$ 的样本 <br><br>
<center>$X^*_1,X^*_2,\dots,X^*_n\backsim F(x;\hat{\beta})$</center>

这种样本可以产生很多个，就可以利用这些样本对总体进行统计推断，其做法与非参数 bootstrap 方法一样，这种方法称为 **参数 bootstrap 法**

&emsp;&emsp;**例2**：已知某种电子元件的寿命服从 **韦布尔分布**，其分布函数为 <br><br>
<center>$F(x)=\begin{cases}1-e^{-(x/\eta)^{\beta}}&x>0\\0&else\end{cases}\qquad\beta>0,\eta>0$</center><br>
&emsp;&emsp;概率密度为 <br><br>
<center>$f(x)=\begin{cases}\dfrac{\beta}{\eta^{\beta}}x^{\beta-1}e^{-(x/\eta)^{\beta}}&x>0\\0&else\end{cases}$</center><br>
&emsp;&emsp;已知 $\beta=2$，且有样本数据

<table border=0 cellpadding=0 cellspacing=0 width=990 style='border-collapse:
 collapse;table-layout:auto;'>
 <col span=10>
 <tr height=18>
  <td style='text-align: center;'>$142.84$</td>
  <td style='text-align: center;'>$97.04$</td>
  <td style='text-align: center;'>$32.46$</td>
  <td style='text-align: center;'>$69.14$</td>
  <td style='text-align: center;'>$85.67$</td>
  <td style='text-align: center;'>$114.43$</td>
  <td style='text-align: center;'>$41.76$</td>
  <td style='text-align: center;'>$163.07$</td>
  <td style='text-align: center;'>$108.22$</td>
  <td style='text-align: center;'>$63.28$</td>
 </tr>
</table>

- 确定参数 $\eta$ 的最大似然估计

&emsp;&emsp;设有样本 $x_1,x_2,\dots,x_n$，似然函数为 <br><br>
<center>$L=\prod\limits^n_{i=1}\dfrac{2}{\eta^2}x_ie^{-(x_i/\eta)^2}=\dfrac{2^n}{\eta^{2n}}\big(\prod\limits^n_{i=1}x_i\big)e^{-(\sum\limits^{n}_{i=1}x_i^2)/\eta^2}$</center><br>
<center>$\ln L=C+[-2n\ln\eta-\dfrac{1}{\eta^2}\sum\limits^{n}_{i=1}x^2_i],\quad C\in\mathbb{C}$</center><br>
&emsp;&emsp;令 $\dfrac{d}{d\eta}\ln L=0$ 可得 $\dfrac{-2n}{\eta}+\dfrac{2}{\eta^3}\sum\limits^n_{i=1}x^2_i=0$，$\hat{\eta}=\sqrt{\dfrac{\sum\limits^{n}_{i=1}x^2_i}{n}}$，以数据代入得 $\eta$ 的最大似然估计为 $\hat{\eta}=100.0696$

- 对于时刻 $t_0=50$，求可靠性 $R(50)=1-F(50)=e^{-(50/\eta)^2}$ 的置信水平分别为 $0.95,0.90$ 的 bootstrap 单侧置信下限

&emsp;&emsp;设 $U\backsim U(0,1)$，令 $U=1-e^{-(X/\eta)^2}$ 有 $X=\eta[-\ln(1-U)]^{\tfrac{1}{2}}=\eta[-\ln U]^{\tfrac{1}{2}}$ 具有参数 $\beta=2,\eta$ 的韦布尔分布，以 $F(x,\hat{\eta})=F(x,100.069)$ 为分布函数产生 $5000$ 个容量为 $10$ 的 bootstrap 样本 <br><br>
<center>$\eta^*_k=\sqrt{\dfrac{\sum\limits^{10}_{i=1}(x^{*_k}_i)^2}{10}}$</center>

&emsp;&emsp;将以上 $5000$ 个 $y$ 自小到大排序，取左起第 $250$ 位得 $\hat{\eta}^*_{(250)}=73.257$，取左起第 $500$ 位得 $\hat{\eta}^*_{(500)}=73.036$，于是在 $t=50$ 时，可靠性 $R(50)$ 的置信水平为 $0.95$ 与 $0.90$ 的 bootstrap 单侧置信下限分别为 <br><br>
<center>$e^{-\tfrac{50}{n^*_{(250)}})^2}=0.6276,\quad e^{-\tfrac{50}{n^*_{(500)}})^2}=0.6702$<center>

---

## 第03节 bootstrap 假设检验方法举例

### 3.1 bootstrap 假设检验的一般形式

&emsp;&emsp;设 $X_1,X_2,\dots,X_n$ 是来自总体 $X\backsim F(x)$ 的独立同分布的样本，假设 $F(x)$ 是否来自某个特定的分布族 $\mathcal{f}_0$，即验证 <br><br>
<center>$H_0:F(x)\in\mathcal{f}_0,\quad H_1:F(x)\notin\mathcal{f}_0$</center>

> $\mathcal{f}_0$ 通常对分布函数 $F(x)$ 有一些约束，比如检验数学期望 $\mu$ 是否等于 $1$，则 $\mathcal{f}_0=(F(x):\int xdF(x)=1)$

&emsp;&emsp;对于上述假设检验问题，假定可以构造统计量 $T_n=T_n(X_1,X_2,\dots,X_n)$，需要确定统计量在原假设下的 **临界值** $c_n$ 来构造拒绝域 $R_n=(x:T_n\ge c_n)$ 使得在原假设下数据落入拒绝域的概率 <br><br>
<center>$P((X_1,X_2,\dots,X_n)\in R_n | H_0)\le a$</center>

$a$ 是用户预设的数值，一般选为 $0.05$，即控制 **第一类错误** 在 $a$ 水平以下，要确定统计量在原假设下的临界值，关键是得到统计量在 **原假设下的分布**，如前说强调的很多时候统计量的精确分布或者渐近分布都是难以获得的，所以考虑其 Bootstrap 近似，其步骤如下

- 根据原始数据 $x_1,x_2,\dots,x_n$，计算统计量的观测值 $t_{obs}=T_n(x_1,x_2,\dots,x_n)$
- 从原假设下的分布族 $\mathcal{f}_0$ 中抽取数据得到 $X_1,X_2,\dots,X_n$，并由此得到 $T^*_n=T_n(X^*_1,X^*_2,\dots,X^*_n)$
- 重复第二步 $B$ 次，从而可以得到 $T^*_{n_1},T^*_{n_2},\dots,T^*_{n_B}$
- 将 $T^*_{n_1},T^*_{n_2},\dots,T^*_{n_B}$ 从小到大排序，将 $T^*_{n(B*(1-a))}$ 近似为统计量在原假设下的临界值

> 上述算法中，最关键和困难的是如何从原假设下的分布族 $\mathcal{f}_0$ 中抽取数据，需要强调的是，对于假设检验问题不能盲目地直接从经验分布函数中抽取数据. 从经验分布函数中抽取数据在原假设下是可以的，因此此时等价于从原假设下的分布族中抽取数据；但在备择假设下，从经验分布函数中抽取数据则不再满足原假设下的约束，此时 Bootstrap 抽样并不能近似统计量在原假设下的分布

### 3.2 单样本均值 bootstrap 检验 

&emsp;&emsp;上述算法中通过比较统计量的观测值和统计量在原假设下的临界值，即通过判断数据是否落入拒绝域，来进行假设检验，另一种等价的或者说信息量更大的方法则是通过计算 $p$ 值：如果 $p$ 值小于预设的 $a$，则拒绝原假设. 所谓 $p$ 值，即在原假设下统计量比观测值更极端的概率，定义为 $P(T_n\ge t_{obs}|H_0)$，根据定义容易知道 $p$ 值可近似为 <br><br>
<center>$\dfrac{1}{B}\sum\limits^{B}_{i=1}I(T^*_{ni}\ge t_{obs})$</center>

&emsp;&emsp;考虑假设检验问题 $H_0:\mu=1$ 这里 $\mu$ 是 $X_1,X_2,\dots,X_n$ 的数学期望，对此一个常见的统计量是 $T$ 统计量，即 $T_n=\dfrac{\sqrt{n}(\bar{X}-1)}{s}$，这里 $\bar{X}$ 和 $s^2$ 分别是 $X_1,X_2,\dots,X_n$ 的样本均值和样本方差，考虑变换 $\tilde{X}_i=X_i-\bar{X}+1$，注意到不管 $E(X_i)$ 是否等于 $1$，$E(\tilde{X}_i)=1$ 恒成立，即不论原假设还是备择假设成立，$\tilde{X}_i$ 总满足原假设下的约束，故而从原假设下的分布族中抽取数据可通过从 $\tilde{X}_i$ 中有放回抽取来进行实现

&emsp;&emsp; Matlab code 如下
```Matlab
function [power1 power2 power3]=ttest(n,mu)

B=400;
for i=1:500
    x=normrnd(mu,1,n,1);   
    test1=sqrt(n)*(mean(x)-1)/std(x);
    powers1(i)=abs(test1)>=tinv(0.975,n-1);
    powers2(i)=abs(test1)>=1.96;
    
    for l=1: B
        xtilde=x-mean(x)+1;
        temp=unidrnd(n,1,n);
        xstar=xtilde(temp(1:n));
        testboot(l)=sqrt(n)*(mean(xstar)-1)/std(xstar);
    end
    pvalue=mean(abs(testboot)>=abs(test1));
    powers3(i)=pvalue<=0.05;
end  
power1=mean(powers1); power2=mean(powers2); power3=mean(powers3);
[power1 power2 power3]
```

&emsp;&emsp;对于上述命令，$\mu=1$ 对应原假设，此时输出结果应该接近 $0.05$；而 $\mu\ne1$ 时对应备择假设，此时输出结果越大越好，原假设下输出结果是 **经验水平**，而备择假设下输出结果是 **经验功效函数值**
