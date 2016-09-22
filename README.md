数据获取 => 数据清理 => 数据分析 => 结果报告 => 发布报告


两个网站
Rpubs
http://rpubs.com
kaggle
https://www.kaggle.com



数据分析
	探索性数据分析
		* 数据分析中的必要步骤
		* 了解数据
		* 作图
	统计推断
		* 基于数据得出正式结论的过程
		* 
	回归分析
		* 线性模型拟合数据
			- 预测变量
			- 结果标量
		* 预测
			
	机器学习 - 分类问题
		* 训练模型 + 预测
		* 分类问题

结果报告
发布结果



开发数据产品

	GoogleVis API
		- R 制作html,调用Google charts
		- 交互式html图表


	Maniputlate

	rCharts
		- 使用R制作交互式javaScrit 可视化产品

	Shiny 
		- 制作嵌入网页的交互式R程序的平台

	Slidify
		- 制作和发布基于R的报告(ppt)
		https://www.shinyapps.io


R 安装 : cran.r-project.org
Rstudio安装 : rstudio.com



包
	* 扩展R基本功能的机制/集成了众多函数
	* CRAN/Bioconductor/Githubdeng 
		- install.packages()
		- install.


		- 加载包
			>library(caret)

获取帮助
	?函数名(R的帮助文档)




第一章:
	数据结构
	数据操作
	构建子集
	重要函数的使用

1. 数据结构
	* 对象的5中基本类型(classes of objects)
		- 字符(character)
		- 数值(numeric: real numbers)
		- 整数(integer)
		- 复数(complex): 1 + 2i
		- 逻辑(logical:True/Flase)

		查看对象类型 : class(obj)


	* 属性(attribute)
		- 名称(name)


2. 向量
	- 只能包含同一类型的对象


3. 矩阵(matrix)	
	- 向量 + 维度属性(整数向量:nrow,ncol)
	- 创建矩阵
		matrix() : 先列后行
		向量+ 维度属性 vector() + dim()
		行拼接 : cbind(),列拼接 : rbind()
		矩阵属性 : attribute()
4. 数组(array)
	- 与矩阵类似, 
	- 


5. 列表(list)
	- 可以包含不同类型的对象
	- 创建列表
		list()


5. 因子(factor)
	- 分类数据/有序 vs. 无序
	- 整数向量 + 标签(label)(优于整数向量)
		Male/Female vs. 1/2
		常用于lm(),glm()


6. 缺失值(missing value)
	-NA/NaN:NaN 属于NA, NA 不属于NaN
	-N/A 有烈性属性:interger NA, character NA等
	is.na(),is.nan()

7. 数据框(data frame)
	- 存储表格数据(tabular data)
	- 视为各元素长度相同的列表
		* 每个元素代表一列数据
		* 每个元素的长度代表行数
		* 元素类型可以不同


8. 日期 与 时间(date,time)
	- 日期:Date
		* julian() : 距离1970-01-01 的天数 / date() / Sys.Date()
		* weekdays() / months() / quarters()

	- 时间:POSIXct / POSIXlt
		* 举例1970-01-01的秒数/ Sys.time()
		* POSIXct : 整数, 常用于存入数据框
		* POSIXlt : 列表, 包含星期, 年 , 月, 日 等信息




构建子集(subsetting)
	* 原始数据(raw dataset) -> 预处理后的数据(clean dataset)
	* 基本方法:
		- [] :  提取一个或者多个类型相同的元素
		- [[]]	:	从列表或数据框中提取元素
		- $	:	按名字从列表或数据框中提取元素







重要函数的梳理

	1. 处理循环
		- R 不仅有for/ while 循环语句, 还有更强大的实现循环的"一句好"函数
		* lapply
			- 可以循环处理列表中的每一个元素
				- lapply(参数) : lapply(列表, 函数/函数名, 其他参数)
			- 总是返回一个列表
		* sapply : 简化结果
			- 结果列表元素长度均为1, 返回向量
			- 结果列表元素长度相同且大于1, 返回矩阵
		* apply
			- 沿着数组的某一维度处理数据
				. 例如: 将函数用于矩阵的行或列
				. 虽然与for/while循环的效率类似, 但是只用了一句话就可以完成.
			- APPly(参数), apply(数组, 维度, 函数/函数名)
		* mapply
			- lapply的多元本
			- mapply(参数) : mapply(函数/函数名,数据, 函数相关的参数);
		* tapply
			- 对向量的子集进行操作	
			- tapply(参数) : tapply(向量, 因子/因子列表,函数/函数名)
		* split
			- 根据因子或因子列表将向量或其他对象分组
			- 通常与lapply一起使用
			- split(参数): split(向量/列表/数据框,因子/因子列表)

	2. 排序
		* sort : 对向量进行排序, 返回拍好序的内容
		* order : 返回排好序的内容的下标 / 多个排序标准


	3. 总结数据信息





完整的数据分析流程


定义研究问题
定义理想的数据集
确定能够获取什么数据
获取数据
清理数据

 	==> 探索性分析(数据可视化), 统计分析/建模(机器学习)等




数值变量的特征和可视化
	* 数据集中趋势的测量
		-- 均值(mean), 中位数(median), 众数(mode)

	* 数据分散趋势的测量
		-- 值域(range: max-min), 方差(variance), 标准差(standardvariance), 四分位距(interquaritle range)

	* 稳健统计量
		-- 是 : 中位数, 四分位差(受极端值影响小)
		-- 否 : 均值, 标准差, 值域(受极端值影响大)

	* 一个变量的可视化
		-- 柱状图, 点图(dot plot)(分布)
		-- 箱图(box plot) (中位数, 分位点,极端值)	

	* 两个变量的关系
		-- 散点图(scatter plot): 方向, 形状, 强度, 极端值


分类变量的特征和可视化
	* 一个分类变量的可视化
		-- 频率表(frequency table) 条形图(bar plot)
	* 两个分类变量的关系
		-- 关联表, 相对频率表
		-- 分段条形图, 相对频率分段条形图

















		

