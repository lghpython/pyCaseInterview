## python 面试题 - 中级能力

### 单选

#### 13.阅读下列代码，输出结果正确的是（B）
```python
import numpy as np
arr = np.array([[1, 2, 3],
[4, 5, 6],
[7, 8, 9],
[7, 8, 9]])
row_means = arr.mean(1)
demeaned = arr - row_means.reshape(4,1)
print(demeaned.mean(1))
```
    A. [0. 0. 0.]
    B. [0. 0. 0. 0.]
    C. [1.33333333 3.33333333 5.33333333 5.33333333]
    D. 编译错误
> 相关知识点：a.mean(1)等同 np.mean(a, axis=1)  row_means = [2. 5. 8. 8.] row_means.reshape(4,1)等于将矩阵转置 矩阵相减：n维矩阵减1维矩阵，会将n维矩阵的每一个维度都减去该一维矩阵 demeaned的值为 [[-1. 0. 1.] [-1. 0. 1.] [-1. 0. 1.] [-1. 0. 1.]] mean(1) axis =1 ：压缩列，对各行求均值，返回 m *1 矩阵

#### 15.下列字符串表示Matplotlib中plot线条颜色、点的形状和类型为红色五角星点短虚线的是（D）

    A. bs-'
    B. 'go-.'
    C. 'r+-.'
    D. r*:

> 相关知识点： 第四个选项中，"r"代表颜色为红色，"*"代表点的形状为星型，":"代表线条为点虚线。故选第四个选项。

#### 16.在Flask中，关于QLAlchemy 查询过滤器的作用描述正确的是（A）

    A. limit: 用特定的值过滤原查询的结果
    B. filter_by(): 把非等值过滤器添加到原查询上，返回一个新查询
    C. filter(): 把等值过滤器添加到原查询上，返回一个新查询
    D. order_by():根据指定条件对原查询结果进行分组，返回一个新查询

> 相关知识点： BC功能反了,D应该为排序


### 多选 

#### 1.Scrapy的回调函数中，解析response并且返回值，则返回值可能是（ABCD ）

    A. 包含解析数据的字典
    B. Item对象
    C. 新的Request对象
    D. 可迭代对象（Items或Request）

> 相关知识点： 在回调函数中，解析response并返回返回值 返回值有四种： 1- 包含解析数据的字典 2- Item对象 3- 新的Request对象（新的Requests也需要制定一个回调函数） 4- 可迭代对象（包含Items或Request）

#### 2.下面关于Python中使用openpyxl对Excel进行写入读取操作错误的是（ AC）

    A. openpyxl.load_Workbook()表示保存工作簿
    B. sheet.append() 表示往工作表写入一行
    C. sheet['A1'].value='冬天' 表示往单元格A1写入数据
    D. wb = openpyxl.Workbook() 表示创建工作簿

> 相关知识点： A选项openpyxl.load_Workbook()表示读取工作簿 C选项sheet['A1'].value='冬天' 表示读取单元格A1的数据，sheet['A1'].='冬天'才是写入数据