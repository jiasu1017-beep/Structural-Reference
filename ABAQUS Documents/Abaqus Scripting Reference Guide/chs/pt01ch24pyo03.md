# 24.3 AbaqusNDarray 对象





AbaqusNDarray 对象是一个从 `numpy.ndarray` 派生的序列对象，用于存储来自 Abaqus 输入文件的数值关键字数据。此对象类似于 `numpy.ndarray` 对象，但数值元素作为标准 Python 对象返回，而不是 `numpy` 数值类型。

数值元素可以是：
- 全部为整数。
- 全部为浮点数。
- 第一列为整数，其他列全部为浮点数。

在最后一种情况下，成员 *colZeroIsInt* 将为 True；在其他两种情况下，它将为 False。





