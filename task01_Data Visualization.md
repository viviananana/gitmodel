# 1.什么是数据可视化
**含义：清晰且美观地表达数据结果信息**

**要点：**
- 图表展示的信息全面且无歧义
- 通俗易懂，不能太专业

# 2.Python三大可视化工具库
## 1.matplotlib
	import matplotlib.pyplot as plt
特征：一句代码相当于图上的一个笔画
**基本参数**
- 创建一个图形对象，设置图形对象的大小：plt.figure(figsize=(6,4))
- 绘制散点图：plt.scatter(x=x, y=sin(x))
- 设置x轴的标签label：plt.xlabel('x')
- 设置y轴标签的label：plt.ylabel('y')
- 设置图表的标题：plt.title('y = sin(x)')
- 展示图表：plt.show()
## 2.seaborn
Seaborn主要用于统计分析绘图，它基于Matplotlib进行了更高级的API封装，更加易用，可作为mpl的补充
## 3.plotnine
优点：采用”图层“概念，一句代码相当于向图像中添加一个图层
缺点：Plotnine只能绘制直角坐标图，无法绘制类似于饼图、环图等图表

# 3.Matplotlib绘图基础
**1.基本元素：**
- 基本绘图类型（graphic primitives）：点 (marker)、线 (line)、文本 (text)、图例 (legend)、网格线 (grid)、 标题 (title)、图片 (image) 等；
- 容器绘图类型（containers）：
	- Figure：最重要的元素，代表**整个图像**，所有的其他元素都是绘制在其上
	- Axes：次重要的元素，代表 **subplot（子图）**，数据都是显示在这个区域，一个Figure至少含有一个Axes对象
	- Axis：代表**坐标轴对象**，本质是一种带装饰的 spines，一般分为 xaxis 和 yaxis，Axis对象主要用于控制数据轴上的刻度位置和显示数值。
	- Spines：表示数据显示区域的边界，可以显示或不显示。
	- Artist：表示任何显示在 Figure 上的元素，Artist 是很通用的概念，几乎任何需要绘制的元素都可以当成是 Artist，但是一个 Artist 只能存在于一个 Axes 之上
[figure示意图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220913204855.png)
[图表元素](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220913205636.png)

matplotlib绘图类型及参数：
<table style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			绘图函数
		</td>
		<td style="padding-right: 8pt; padding-left: 8pt;">
			图表类型
		</td>
		<td style="padding-right: 10pt; padding-left: 10pt;">
			绘图函数参数
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.plot()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			折线图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x&nbsp;
				</li>
				<li>
					y
				</li>
				<li>
					color 线条颜色
				</li>
				<li>
					linestyle线条类型
				</li>
				<li>
					linewidth 线条宽度
				</li>
				<li>
					marker 点的形状
				</li>
				<li>
					markeredgecolor 点的边框颜色
				</li>
				<li>
					markeredgewidth 点的边框的宽度
				</li>
				<li>
					markerfacecolor 点的填充颜色
				</li>
				<li>
					markersize 点的大小
				</li>
				<li>
					label 线图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.scatter()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			散点图、气泡图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					y
				</li>
				<li>
					s 散点的大小（size）
				</li>
				<li>
					c 散点的颜色（color）
				</li>
				<li>
					marker 散点的形状类型
				</li>
				<li>
					linewidths 散点的边框宽度&nbsp;
				</li>
				<li>
					edgecolors 散点的边框颜色
				</li>
				<li>
					label 点图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.bar()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			柱状图、堆叠柱状图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					height 柱子的高度
				</li>
				<li>
					width 柱子的宽度
				</li>
				<li>
					align 柱子与x的对齐方式，有：{'center'居中对齐, 'edge'左侧对齐}，默认为'center'
				</li>
				<li>
					color 柱子的填充颜色
				</li>
				<li>
					edgecolor 柱子边框的颜色
				</li>
				<li>
					linewidth 柱子边框线的宽度
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.barh()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			横向柱状图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					y
				</li>
				<li>
					height 柱子的高度
				</li>
				<li>
					width 柱子的宽度
				</li>
				<li>
					align 柱子与x的对齐方式
					<br>
				</li>
				<li>
					color 柱子的填充颜色
				</li>
				<li>
					edgecolor 柱子边框的颜色
				</li>
				<li>
					linewidth 柱子边框线的宽度
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.hist()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			直方图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					bins 划分组数
				</li>
				<li>
					range 统计的范围，默认为(x.min(), x.max())
				</li>
				<li>
					density 频数直方图还是频率直方图
				</li>
				<li>
					align&nbsp;柱子与x的对齐方式
				</li>
				<li>
					color 颜色
				</li>
				<li>
					label 直方图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.boxplot()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			箱线图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					notch 是否凹口展示
				</li>
				<li>
					sym 散点的形状
				</li>
				<li>
					vert 水平箱线图还是竖向箱线图
				</li>
				<li>
					widths 箱子的宽度
				</li>
				<li>
					label 箱线图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.fill_between()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			面积图、填充图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					y
				</li>
				<li>
					facecolor 填充颜色
				</li>
				<li>
					edgecolor 边缘线条颜色
				</li>
				<li>
					linewidth 边缘线宽度
				</li>
				<li>
					where 填充的范围
				</li>
				<li>
					interpolate&nbsp;interpolate只有在使用了where参数同时两条曲线交叉时才有效, 使用这个参数会把曲线交叉处也填充使得填充的更完整
				</li>
				<li>
					alpha 透明度
				</li>
				<li>
					label 面积图的标签（常配合legend）<wbr>
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.stackplot()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			堆叠面积图、河流图
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x&nbsp;尺寸为N的一维数组&nbsp;
				</li>
				<li>
					y&nbsp;尺寸为(M,N)的二维数组&nbsp;
				</li>
				<li>
					baseline 基线，取值范围为{'zero', 'sym', 'wiggle', 'weighted_wiggle'}：'zero'：以0为基线，比如绘制简单的堆积面积图；'sym'：以0上下对称，有时被称为主题河流图；'wiggle'：所有序列的斜率平方和最小；'weighted_wiggle'： 类似于'wiggle'，但是增加各层的大小作为权重。绘制出的图形也被称为流图（streamgraph）。
				</li>
				<li>
					堆叠面积图的标签（常配合legend）
				</li>
			</ul>
			<wbr>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.pie()&nbsp;<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			饼状图<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					<font><b>x&nbsp;</b> (每一块)的比例，如果sum(x) &gt; 1会使用sum(x)归一化</font><wbr>
				</li>
				<li>
					<font>colors 填充的颜色</font>
				</li>
				<li>
					<font>labels&nbsp;</font><font>(每一块)饼图外侧显示的说明文字</font>
				</li>
				<li>
					<font>radius&nbsp;控制饼图半径</font>
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.errorbar()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			误差折线图&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					y
				</li>
				<li>
					yerr y轴的误差范围
				</li>
				<li>
					xerr x轴的误差范围
				</li>
				<li>
					fmt fmt参数的值和plot方法中指定点的颜色，形状，线条风格的缩写方式相同，如：<font>fmt='co--'</font><wbr>
				</li>
				<li>
					<font>ecolor 误差线的颜色</font>
				</li>
				<li>
					<font>elinewidth 误差线的宽度</font>
				</li>
				<li>
					<font>ms 数据点的大小</font>
				</li>
				<li>
					<font>mfc 数据点的填充颜色</font>
				</li>
				<li>
					<font>mec 数据点边缘颜色</font>
				</li>
				<li>
					<font>capthick 误差线的粗细</font>
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.axhline()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			水平直线
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					y
				</li>
				<li>
					xmin&nbsp;取值位于[0,1]之间，取值0时在图的左边界，取值1时在图的右边界
				</li>
				<li>
					xmax&nbsp;取值位于[0,1]之间，0取值时在图的左边界，取值1时在图的右边界
				</li>
				<li>
					color 线条颜色
				</li>
				<li>
					linestyle 线条类型
				</li>
				<li>
					linewidth 线条宽度
				</li>
				<li>
					label 线图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.axvline()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			竖向直线
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x
				</li>
				<li>
					ymin&nbsp;取值位于[0,1]之间，取值0时在图的左边界，取值1时在图的右边界
				</li>
				<li>
					ymax&nbsp;取值位于[0,1]之间，0取值时在图的左边界，取值1时在图的右边界
				</li>
				<li>
					color 线条颜色
				</li>
				<li>
					linestyle 线条类型
				</li>
				<li>
					linewidth 线条宽度
				</li>
				<li>
					label 线图的标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.axhspan()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			水平矩形带
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					ymin 矩形条带下边界的y坐标
				</li>
				<li>
					ymax 矩形条带上边界的y坐标
				</li>
				<li>
					facecolor 填充颜色
				</li>
				<li>
					alpha 透明度
				</li>
				<li>
					edgecolor 边缘线条颜色
				</li>
				<li>
					linestyle 线条类型
				</li>
				<li>
					linewidth 线条宽度
				</li>
				<li>
					label 条带标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.axvspan()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			竖直矩形带
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					xmin 矩形条带左边界的x坐标
				</li>
				<li>
					xmax 矩形条带右边界的x坐标
				</li>
				<li>
					facecolor 填充颜色
				</li>
				<li>
					alpha 透明度
				</li>
				<li>
					edgecolor 边缘线条颜色
				</li>
				<li>
					linestyle 线条类型
				</li>
				<li>
					linewidth 线条宽度
				</li>
				<li>
					label 条带标签（常配合legend）
				</li>
			</ul>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.text()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			文本
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					x：文本位置的x坐标
				</li>
				<li>
					y：文本位置的y坐标
				</li>
				<li>
					string：文本
				</li>
				<li>
					fontdict 使用字典dict形式定义文本的字体属性，如：
				</li>
			</ul>
			fontdict =&nbsp;
			<br>
			dict(
			<br>
			fontsize=12,
			<br>
			color='r',
			<br>
			family='monospace',<i>#字体,可选'serif', 'sans-serif', 'cursive', 'fantasy', 'monospace'</i>
			<br>
			weight='bold',<i>#磅值，可选'light', 'normal', 'medium', 'semibold', 'bold', 'heavy', 'black'</i>&nbsp;
			<br>
			)<wbr>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			plt.annotate()&nbsp;
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			添加带箭头的文本标注
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<ul>
				<li>
					s 标注的文本内容
				</li>
				<li>
					xy 代表标注点的坐标位置
				</li>
				<li>
					xytext 标注的文字的坐标<wbr>
				</li>
				<li>
					arrowprops 箭头参数,参数类型为字典dict，如：<wbr>
				</li>
			</ul>
			arrowprops=dict(
			<br>
			arrowstyle = '-&gt;',&nbsp; # 箭头的风格
			<br>
			connectionstyle = 'arc3,&nbsp;# 连接方式
			<br>
			rad=0.2' # 弯曲的角度
			<br>
			)<wbr>
		</td>
	</tr>
</table>

# 4.Plotnine绘图基础
Plotnine中的图层可以分为：必备图层和可选图层

**1. 必选图层**
- ggplot()图层：底层绘图函数，ggplot()函数可以将绘图和数据分离，在ggplot内可以设置数据以及数据的映射，如：ggplot(data, aes(x='col_x', y='y_value', fill='col_class'))。因此，在ggplot()中，除了设置数据外，还可以设置变量的映射aes()，用来表示x和y，还可以在aes()内控制颜色color、大小size和形状shape等等。
- geom_xxx()图层：几何对象，即在图中实际看到的图形元素，总结：
<table style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			变量个数
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			变量类型
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_xxx()函数
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			函数作用
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			连续型
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_histogram ()
			<br>
			geom_density()
			<br>
			geom_dotplot()
			<br>
			geom_freqpoly()
			<br>
			geom_qq()
			<br>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			直方图
			<br>
			密度图
			<br>
			点图
			<br>
			频次图
			<br>
			qq图<wbr>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			离散型
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_bar()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			柱状图
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			x连续型-y连续型
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_point()
			<br>
			geom_area()
			<br>
			geom_line()
			<br>
			geom_jitter()
			<br>
			geom_smooth()
			<br>
			geom_label()
			<br>
			geom_text()
			<br>
			geom_bin2d()
			<br>
			geom_density2d()
			<br>
			geom_step()
			<br>
			geom_quantile()
			<br>
			geom_rug()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			散点图
			<br>
			面积图
			<br>
			线图
			<br>
			抖动散点图
			<br>
			平滑图
			<br>
			带背景的文本注释图
			<br>
			文字注释
			<br>
			阶梯图
			<br>
			分位数回归图
			<br>
			突出xy位置的散点图<wbr>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			x离散-y连续
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_boxplot()
			<br>
			geom_violin()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			箱线图
			<br>
			提琴图<wbr>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			x离散-y离散
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_count()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			统计直方图
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			3
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			x连续-y连续-z连续
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			geom_tile()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			热力图
		</td>
	</tr>
</table>

**2. 可选图层：用于美化图表图层和变换坐标系相关图层**
- scale_xxx()图层：标度（scale）是用于调整数据映射的图形属性，scale_xxx()获取数据并对其进行调整以适应视觉的不同方面，即长度、颜色、大小和形状等。
<table style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<b>连续型continuous</b>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<b>离散型discrete</b>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<b>自定义manual</b>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<b>同一型identity</b>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			坐标轴标度scale_x_xxx()/scale_y_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_x_continous()
			<br>
			scale_y_continous()
			<br>
			scale_x_log10()
			<br>
			scale_y_log10()
			<br>
			scale_x_sqrt()
			<br>
			scale_y_sqrt()
			<br>
			scale_x_reverse()
			<br>
			scale_y_reverse()
			<br>
			scale_x_date()
			<br>
			scale_y_date()
			<br>
			scale_x_datetime()
			<br>
			scale_y_datetime()
			<br>
			scale_x_timedelta()
			<br>
			scale_y_timedelta()
			<br>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_x_discrete()
			<br>
			scale_y_discrete()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			颜色标度sclae_color_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_color_continous()
			<br>
			scale_color_distiller()
			<br>
			scale_color_gradient()
			<br>
			scale_color_gradient2()
			<br>
			scale_color_gradientn()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_color_discrete()
			<br>
			scale_color_brewer()
			<br>
			scale_color_hue()
			<br>
			<font color="#333333">scale_color_grey()<wbr></font><font color="#333333">scale_color_gray()</font><wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<font color="#333333">scale_color_manual()</font>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			<font color="#333333">scale_color_identity()</font>
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			填充标度scale_fill_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_fill_continuous()
			<br>
			scale_fill_distiller()
			<br>
			scale_fill_gradient()
			<br>
			scale_fill_gradient2()
			<br>
			scale_fill_gradientn()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_fill_discrete()
			<br>
			scale_fill_brewer()
			<br>
			scale_fill_hue()
			<br>
			scale_fill_gray()
			<br>
			scale_fill_grey()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_fill_manual()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_fill_identity()
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			大小标度scale_size_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_size()
			<br>
			scale_size_area()
			<br>
			scale_size_radius()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_size_manual()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_size_identity()
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			透明度标度scale_alpha_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_alpha()
			<br>
			scale_alpha_continuous()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_alpha_discrete()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_alpha_manual()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_alpha_identity
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			线条样式标度scale_linetype_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_linetype()
			<br>
			scale_linetype_discrete()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_linetype_manual()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_linetype_identity()
		</td>
	</tr>
	<tr>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			形状标度scale_shape_xxx()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_shape()
			<br>
			scale_shape_discrete()<wbr>
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_shape_manua()
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			scale_shape_identity(
		</td>
	</tr>
	<tr>
		<td colspan="5" style="padding-right: 3pt; padding-left: 3pt;">
			参数列表&nbsp; &nbsp; &nbsp; &nbsp;lims()&nbsp; &nbsp;&nbsp;xlim()&nbsp; &nbsp;&nbsp;ylim()&nbsp; &nbsp; &nbsp;&nbsp;expand_limits()&nbsp; &nbsp; &nbsp;guides()&nbsp; &nbsp; &nbsp;&nbsp;guide()&nbsp; &nbsp; &nbsp;guide_legend()&nbsp; &nbsp; &nbsp; &nbsp;guide_colorbar()
		</td>
	</tr>
</table>

- coord_xxx()图层：坐标系图层
    - coord_cartesian()
    - coord_equal()
    - coord_fixed()
    - coord_flip()
    - coord_trans()
- facet_xxx()图层：分面图层，主要是将一个图按照某个变量分解成多个图，主要是对比在同一变量的不同取值下，关系图表的变化
     - facet()
     - facet_grid()
     - facet_null()
     - facet_wrap()
- theme()图层：主题调整，主要是设定主题风格。主要有以下主题：
     - theme()
     - theme_538()
     - theme_bw()
     - theme_classic()
     - theme_dark()
     - theme_gray()
     - theme_grey()
     - theme_light()
     - theme_linedraw()
     - theme_matplotlib()
     - theme_minimal()
     - theme_seaborn()
     - theme_void()
     - theme_xkcd()

# 5.基本图表的Quick Start
## 5.1 类别型图表
- 特征：X为类别型数据、Y为数值型数据
- 常见图表：柱状图、横向柱状图（条形图）、堆叠柱状图、极坐标的柱状图、词云、雷达图、桑基图等
1. 当类别型数据为二维数据，例如城市+年份-->房价，则可使用：
	- 多系列柱状图
	- 哑铃图
	- 坡度图（简化版折线图）
2. 当每个X具有多个属性Y且需进行对比时，例如员工职场能力分数，则可使用：
	- 雷达图（仅matplotlib）

## 5.2 关系型图标
特征：体现XY两个数值之间的关系
1. 散点图：
- 变量之间是否存在关联关系；
- 如果存在关联关系，那么变量之间的关联关系是正向关联还是负向关联；
- 如果存在变量关系，那么是线性关联还是非线性关联；
- 是否存在趋势之外的点：离群点；

2. 进阶散点图：添加**回归趋势线**，使趋势性规律更具说服性
[趋势散点图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915152115.png)
3. Q-Q图和P-P图：
4. 聚类散点图
5. 相关系数矩阵图(heatmap)：适用于体现多维度之间的关系，每个点都代表两变量之间的相关系数
[heatmap](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915161631.png)
## 5.3 数据分布型图表
用于描述数据的密集或者稀疏情况
1. 统计直方图
2. 核密度图：用连续区间来描述数据分布
[核密度图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915162521.png)
3. 箱线图：箱子宽度代表数据量
[箱线图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915162510.png)
4. 提琴图：箱线图和核密度图的结合（如下图所示）
[提琴图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915163254.png)
5. 饼图/环饼图（仅matplotlib）
## 5.4 时间序列型图表
1. 时间序列线图：包括单序列与多序列折线图
2. 日历图：反映数据的周期性信息，参考ggplot2使用方法，beautiful！
[日历图](https://github.com/viviananana/gitmodel/blob/3fb0cfe0b9091b19434f1ddb2def7d4cfd21e3ff/Pasted%20image%2020220915165327.png)
## 5.5 空间分布图表
*暂时用不着，而且有点难就先搁这嘿嘿*

# 小结
1. 初步了解python的三个绘图包，并对matplotlib和plotnine进行各图例的绘制语法对比
2. 作者梳理的基本图表类型很清晰，帮助我理解不同图表的应用场景，在基本数据呈现方式基础上，还补充了一些令人眼前一亮的图表，例如heatmap、日历图、提琴图等，为读研写paper展示数据提供了新思路，很感谢❤
3. 目前对plotnine语法还比较生疏（之前没有接触过r以及ggplot2），希望自己再多加练习


### 运行代码时遇到的问题
-  jupyter notebook安装库不成功
	- 要使用 !pip install [package]，注意加上感叹号


### 参考资料：
[gitmodel_lesson](https://github.com/Git-Model/Modeling-Universe/tree/main/Data%20Analysis%20and%20Statistical%20Modeling)
