# 1.推断/假设检验
## 1.1 t检验-单参数检验
### p值
p值是在本次分析的样本观测值下，给出的能拒绝原假设的**最小显著性水平**，它只与样本观测值和我们做的假设检验有关。p值越小越可以拒绝原假设，
例如：如果p值为0.001，比0.01的显著性水平还要小，我们认为在0.01的显著性水平下我们也可以拒绝原假设；而如果p值为0.025，比0.01的显著性水平要大，但小于0.05，则我们认为在0.05的显著性水平下我们可以拒绝原假设，但在0.01显著性水平下不可以拒绝。
p值的形式与我们做的备择假设$H_1$有关：

若$H_{1}: \beta_{j} \neq \beta_{j 0}$，则：$pvalue=P\left( \left| t_{n-k-1} \right|>\left| \frac{\hat{\beta}_j-\beta _{j0}}{se\left( \hat{\beta}_j \right)} \right| \right)$

若$H_{1}: \beta_{j} > \beta_{j 0}$，则：$pvalue=P\left( t_{n-k-1}>\frac{\hat{\beta}_j-\beta _{j0}}{se\left( \hat{\beta}_j \right)} \right)$

若$H_{1}: \beta_{j} < \beta_{j 0}$，则：$pvalue=P\left( t_{n-k-1}<\frac{\hat{\beta}_j-\beta _{j0}}{se\left( \hat{\beta}_j \right)} \right)$

可以看到，p值本质上是一种累积概率，且对于同一个$\beta_{j 0}$而言，双边检验的p值为单边检验的两倍
summary()中的p值，正是系数0值双边检验的p值
## 1.2 t检验-多参数检验
可通过换元法变换模型，转换检验问题为单参数的显著性检验问题
*注意合并变量的写法：
```
wage1_lm=sm.formula.ols('lwage~jc+I(jc+univ)+exper',data=wage1).fit()
# 注意，如果我们要将jc与univ的和当做一个新变量的话，需要使用I()
print(wage1_lm.summary())
```

## 1.3 F检验
在实际问题的假设检验中，我们除了对某个参数单独进行检验外，还需要对多个参数同时进行检验；多个参数做联合显著性检验**完全不等价于**多个参数分开做显著性t检验，于是引入新方法——F检验
### F统计量的定义
- 约束模型与无约束模型，比较两者差异程度
- 称原模型为无约束模型(unrestricted model)，然后将原假设$H_0$成立下的条件代入无约束模型，得到的模型称为有约束模型(restricted model)
- 无约束模型相较于有约束模型多了三个参数与变量。一般而言，模型变量越多，对训练集数据的变异解释程度会越高，拟合优度会越好，进而残差平方和会减小。如果两个模型残差平方和的差异足够大，说明原假设约束的加入是模型产生了显著性的变化，这意味着原假设是显著的！

基于这种思考，统计学家们定义了回归分析中的F检验统计量：
$$
F=\frac{\left( RSS_r-RSS_{ur} \right) /q}{RSS_{ur}/(n-k-1)}\sim F_{q,n-k-1}
$$
它服从自由度为$q$与$n-k-1$的F分布，其中$q$为有效约束个数，$n-k-1$为无约束模型自由度。
F检验拒绝原假设的判别规则：
$$
F>F_{q,n-k-1}\left( 1-\alpha \right) 
$$
- 代码实现：
	- 方法一：按公式计算模型RSS、F值、F分布分位点、p值
	- 方法二：使用anova_lm函数，可直接输出F值与p值
	```
	from statsmodels.stats.anova import anova_lm
	anova_lm(mlb_r,mlb_ur) # 注意，是有约束在前，无约束在后
	```