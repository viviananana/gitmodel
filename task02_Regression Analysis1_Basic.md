# 1. 回归模型总述
## 1.1 回归思想与一般回归模型
1. 横截面数据：横截面数据是回归分析最主要的分析数据类型，它可以视为在同一时间点（或抽样时间差异可以被忽略）上对多个抽样个体的观测数据，我们记第$i$个个体的观测数据为$(x_i,y_i)$
2. 回归思想——条件均值建模

3. 一般回归模型
$$
y=E(y|x)+u
$$
- 推论1：随机误差的无条件期望$E(u)=0$——这表示其他因素对$y$的平均影响为0
- 推论2：随机误差$u$与自变量$x$协方差$Cov(u,x)=0$——这表示其他因素与参与回归的$x$不相关
## 1.2 线性回归模型
线性回归模型可表示为：
$$
y=\beta_{0}+\beta_{1} x_{1}+\cdots+\beta_{p} x_{p}+u, \quad E\left(u \mid x_{1}, \cdots, x_{p}\right)=0
$$
回归分析主要研究如何有效地估计模型中的参数$\hat{\beta}_i$，并利用模型进行推断与预测
- 简单线性回归：1个因素对y的影响
$$
y=\beta_{0}+\beta_{1} x+u, \quad E(u \mid x)=0
$$
$\beta_{1}=\frac{\Delta m(x)}{\Delta x}$，可理解为$x$每增加一个单位，$y$平均增加$\beta_1$个单位
简单线性回归的局限性：因变量𝑦通常受多个因素影响，这些因素之间可能彼此之间存在线性相关性（后续的学习中我们将这种现象称为多重共线性）

- 多元线性回归：
$$
y=\beta_{0}+\beta_{1} x_{1}+\cdots+\beta_{k} x_{k}+u
$$
$u$为随机误差项，它表示除$x_1$,…,$x_k$以外的其他因素对因变量$y$的影响，且同样满足假设：
$$
E\left(u \mid x_{1}, \cdots, x_{k}\right)=0
$$
$\beta_i=\frac{\partial m\left( x \right)}{\partial x_i}$是回归函数对变量$x_i$的偏导数，它被解释为**在保持其他自变量不变的情况下，$x_i$每增加一单位，$y$平均增加$\beta_i$个单位**

# 2. 模型系数的估计方法——OLS估计及其性质
普通最小二乘估计法(Ordinary Least Squares, OLS)
## 2.1 OLS思想与原理
直观来说，最佳的拟合直线应该尽可能的贴合样本点，我们要选出一条离所有样本点距离的总和最小的直线。
我们将模型回归参数分别记为$\hat{\beta}_{0}$,$\hat{\beta}_{1}$ ，并定义 $\hat{y}_{i}=\hat{\beta}_{0}+\hat{\beta}_{1} x_{i}$ 为样本在自变量为 $x_i$ 下的拟合值，记样本实际观测值$y_i$与拟合值$\hat{y}_{i}$之差为拟合残差：$\hat{u}_{i}=y_{i}-\hat{y}_{i}$。

OLS对距离的定义是：残差的平方 ${\hat{u}_i}^2$ 。因此OLS估计的思想是：**OLS估计求得的系数$\hat{\beta}_{0}$、$\hat{\beta}_{1}$，将使直线与所有样本的拟合残差的平方和最小**，多元线性回归即：

$$
\left( \hat{\beta}_0,\cdots ,\hat{\beta}_k \right) =\mathrm{arg}\min \sum_{i=1}^n{\left( y_i-\hat{\beta}_0-\hat{\beta}_1x_{1i}-\hat{\beta}_kx_{ki} \right) ^2}
$$

## 2.2 OLS求解
记目标函数为：

$$
Q\left(\hat{\beta}_{0}, \hat{\beta}_{1}, \cdots, \hat{\beta}_{k}\right)=\sum_{i=1}^{n}\left(y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i 1}-\cdots-\hat{\beta}_{k} x_{i k}\right)^{2}
$$

这是一个以 $(\hat{\beta}_{0}, \hat{\beta}_{1}, \cdots, \hat{\beta}_{k})$ 作为未知变量的多元函数，**我们要求得最小值点，可以令各元偏导数等于0**，构建一个$k+1$维的方程组求解：

$$
\begin{aligned}
&\sum_{i=1}^{n}\left(y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i 1}-\cdots-\hat{\beta}_{k} x_{i k}\right)=0 \\
&\sum_{i=1}^{n}\left(y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i 1}-\cdots-\hat{\beta}_{k} x_{i k}\right) x_{i 1}=0 \\
&\sum_{i=1}^{n}\left(y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i 1}-\cdots-\hat{\beta}_{k} x_{i k}\right) x_{i 2}=0 \\
&\cdots \quad \cdots \\
&\sum_{i=1}^{n}\left(y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i 1}-\cdots-\hat{\beta}_{k} x_{i k}\right) x_{i k}=0
\end{aligned}
$$

以上方程组中，每个方程有$k+1$个自变量，且有$k+1$个方程，根据线性代数的知识，我们可以求得$(\hat{\beta}_{0}, \hat{\beta}_{1}, \cdots, \hat{\beta}_{k})$的唯一解
## 2.3 拟合优度
在探讨这个问题前，我们先引入几个简单而又重要的概念：

- TSS(Total sum of squares)，总平方和——度量了因变量$y$的总样本变异
$$
T S S=\sum_{i=1}^{n}\left(y_{i}-\bar{y}\right)^{2}
$$

- ESS(Explained sum of squares)，解释平方和——度量了模型拟合值$\hat{y}$的总变异，即解释了的变异
$$
E S S=\sum_{i=1}^{n}\left(\hat{y}_{i}-\bar{y}\right)^{2}
$$

- RSS(Resiual sum of squares)，残差平方和——度量了“剩余信息”，即未被解释的变异
$$
R S S=\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}
$$
三种平方和的关系：$TSS=RSS+ESS$，说明：总变异可以被拆分为解释了变异+未被解释的变异
- R方：用“解释变异的比例”衡量回归模型拟合优度
$$
R^{2}=\frac{E S S}{T S S}
$$
## 2.4 OLS估计的代数性质
==todo==
# 3. 经典线性模型假设下OLS估计的性质
## 3.1 经典线性模型假设-CLM假设
1. **总体模型假设**
$$
y=\beta_{0}+\beta_{1} x_{1}+\beta_{2} x_{2}+\cdots+\beta_{k} x_{k}+u
$$
假定了我们正确地判断了因变量和自变量之间的关系——既正确设定了模型形式为上述的**线性形式**，又正确纳入了所有自变量
2. **随机误差$u$条件均值零假设**
所有非自变量的其他因素（误差）都与自变量线性无关
3. **随机抽样假设**
ｎ个样本均为随机抽样样本，彼此之间相互独立
4. **非完全共线性假设（满秩）**
这些样本的所有自变量间不能存在有完全共线性，即不能存在某一自变量可由其余自变量进行线性表示的情况
5. **$u$同方差假设**
随机误差$u$的条件方差恒为一个常数，即
$$
\operatorname{Var}\left(u \mid x_{1}, \cdots, x_{k}\right)=\sigma^{2}
$$
6. ****$u$正态性假设**
该假设假定随机误差$u$在任何自变量$x$已知的条件下服从正态分布（2与5的结合）
$$
u \mid x \sim N\left(0, \sigma^{2}\right)
$$
## 3.2 OLS估计的性质-最优的线性无偏估计
假定的正确模型：
$$
y=\beta_{0}+\beta_{1} x_{1}+\cdots+\beta_{k} x_{k}+u
$$
模型估计的模型：
$$
\hat{y}=\hat{\beta}_0+\hat{\beta}_1x_1+\cdots +\hat{\beta}_kx_k
$$
理想模型要求达到：
- 各估计系数$\hat{\beta}$都尽可能接近真实系数$\beta$；
- 并且使用同一总体的不同取样样本进行估计时，估计出来的系数越稳定越好

---
*准备组会汇报好累olz 明天补上*

# 小结
1. 复习线性回归模型，学习了回归思想
2. 学习了OLS最小二乘法估计，以及残差、RSS、TSS等统计量的定义
3. 在满足CLM假设的前提下，OLS估计是经典线性模型最优的参数估计法

*显示不了公式why？？安装了MathJax 3 Plugin for Github呀。。。looks like shit
