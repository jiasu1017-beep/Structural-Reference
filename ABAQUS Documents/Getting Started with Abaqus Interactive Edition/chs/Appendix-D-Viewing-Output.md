# 附录D 查看分析输出结果

本附录介绍如何在Abaqus/Viewer中对有限元分析结果进行后处理，包括显示变形、应力云图、动画制作以及数据提取等操作。

---

## D.1 结果可视化基础

### D.1.1 打开输出数据库

1. 完成分析后，在 **Result** 菜单中选择 **Open ODB**
2. 浏览到 `.odb` 文件位置
3. 点击 **OK** 打开输出数据库

### D.1.2 常用显示选项

| 选项 | 位置 | 功能 |
|------|------|------|
| 变形图 | **Result** → **Plot** → **Deformed Shape** | 显示模型变形轮廓 |
| 轮廓图 | **Result** → **Plot** → **Contours** → **On Deformed Shape** | 显示云图 |
| 单元/节点 | **Result** → **Plot** → **Mesh** | 显示网格 |
| 符号图 | **Result** → **Plot** → **Symbols** | 显示矢量/张量符号 |

---

## D.2 变形和位移分析

### D.2.1 显示变形形状

```python
# 在Abaqus/CAE中查看变形
session.viewports['Viewport: 1'].odbDisplay.display(
    displayMode=DEFORMED)
session.viewports['Viewport: 1'].odbDisplay.setValues(
    step='ApplyLoad',
    frame=1)
session.viewports['Viewport: 1'].odbDisplay.plot(
    deformationScale=FACTOR,
    scaleFactor=10.0)
```

### D.2.2 位移结果说明

- **U1, U2, U3**：节点在X, Y, Z方向的位移分量
- **UR1, UR2, UR3**：节点绕X, Y, Z轴的转角分量
- **U**：合位移大小

### D.2.3 变形动画制作

1. 在 **Result** → **Animation** → **Track**
2. 选择要动画的步骤和帧范围
3. 设置播放速度
4. 点击 **Play** 播放动画

---

## D.3 应力/应变结果

### D.3.1 应力云图

```python
# 显示Mises应力云图
session.viewports['Viewport: 1'].odbDisplay.display(
    displayMode=CONTOURS)
session.viewports['Viewport: 1'].odbDisplay.setValues(
    step='ApplyLoad',
    frame=1)
session.viewports['Viewport: 1'].odbDisplay.plot(
    symbol=SINGLE,
    symbolType=VECTOR)
```

### D.3.2 常用应力分量

| 符号 | 说明 |
|------|------|
| S11, S22, S33 | 正应力分量 |
| S12, S13, S23 | 剪应力分量 |
| S-Mises | Mises等效应力 |
| S-Mises | 最大主应力 |
| S-Min | 最小主应力 |

### D.3.3 应变结果

| 符号 | 说明 |
|------|------|
| E11, E22, E33 | 正应变分量 |
| E12, E13, E23 | 剪应变分量 |
| PE-Mises | 等效塑性应变 |
| PEEQ | 等效塑性应变率 |

---

## D.4 路径结果提取

### D.4.1 定义路径

```python
# 在Abaqus/Viewer中定义路径

# 方法1：沿边缘定义路径
session.viewports['Viewport: 1'].odbDisplay.paths.create(
    name='EdgePath',
    type=EDGE,
    edges=(edge1, edge2))

# 方法2：定义XYZ路径
session.viewports['Viewport: 1'].odbDisplay.paths.create(
    name='XPath',
    type=POINT_LIST,
    pointList=((0, 0, 0), (0.1, 0, 0), (0.2, 0, 0)))

# 方法3：沿分割线定义
session.viewports['Viewport: 1'].odbDisplay.paths.create(
    name='CutPath',
    type=CUTPLANE,
    cutplaneNormal=XAXIS,
    cutplanePoint=(0.5, 0, 0))
```

### D.4.2 沿路径绘图

```python
# 沿路径绘制应力分布
session.viewports['Viewport: 1'].odbDisplay.paths['EdgePath'].plot(
    variable=('S', 'Mises'))
```

### D.4.3 导出路径数据

```python
# 导出路径数据到文件
path = session.viewports['Viewport: 1'].odbDisplay.paths['EdgePath']
data = path.getScalarData(
    variable=('S', 'Mises'),
    step=1,
    frame=1)

# 保存到CSV文件
import csv
with open('stress_along_path.csv', 'w') as f:
    writer = csv.writer(f)
    writer.writerow(['Position', 'S-Mises'])
    for point, value in zip(data[0], data[1]):
        writer.writerow([point, value])
```

---

## D.5 XY 数据绘图

### D.5.1 创建XY数据

```python
# 创建历史输出XY数据
session.viewports['Viewport: 1'].odbDisplay.historyPoints.create(
    name='CenterPoint',
    vertices=(centerVertex, ))

session.viewports['Viewport: 1'].odbDisplay.xyData.create(
    name='Displacement',
    data=session.viewports['Viewport: 1'].odbDisplay.historyPoints['CenterPoint'].getData(
        variable='U2',
        step='ApplyLoad'))
```

### D.5.2 绘制XY曲线

```python
# 绘制时间-位移曲线
session.viewports['Viewport: 1'].odbDisplay.xyData.plot(
    xyData=(
        session.viewports['Viewport: 1'].odbDisplay.xyData['Displacement'],
    ),
    title='Load-Displacement Curve',
    xAxisLabel='Time (s)',
    yAxisLabel='Displacement U2 (m)')
```

### D.5.3 保存XY数据

```python
# 保存XY数据到文件
xyData = session.viewports['Viewport: 1'].odbDisplay.xyData['Displacement']

# 导出为文本文件
session.xyDataObjects['Displacement'].write(
    fileName='displacement.txt',
    append=OFF,
    format=TABLE)

# 导出为CSV格式
session.xyDataObjects['Displacement'].write(
    fileName='displacement.csv',
    append=OFF,
    format=CSV)
```

---

## D.6 结果报告生成

### D.6.1 生成文本报告

```python
# 生成分析结果报告
odb = session.odbs['Model.odb']

# 获取指定位置的应力
session.viewports['Viewport: 1'].odbDisplay.setValues(
    step='ApplyLoad',
    frame=1)

# 生成报告
rpt = session.Report(
    queue=(session.viewports['Viewport: 1'].odbDisplay, ),
    plot=ON,
    reportFormat=PRINT,
    numberOfDigits=6)

session.writeReport(
    reportName='analysis_results.txt',
    reportBody=rpt)
```

### D.6.2 查询工具

使用 **Query** 工具可以快速查看特定位置的结果：

1. **Tools** → **Query**
2. 选择查询类型：
   - **Probe**：查询节点/单元的数值
   - **Probe Values**：查询选中点的所有分量
   - **ODB Information**：查看模型信息

---

## D.7 结果比较

### D.7.1 叠加显示

```python
# 在同一视图中显示多个结果
session.viewports['Viewport: 1'].odbDisplay.plotOverlay(
    odb1=(odb1, 'ApplyLoad', 1),
    odb2=(odb2, 'ApplyLoad', 1))
```

### D.7.2 差异显示

```python
# 比较两个模型的应力差异
session.viewports['Viewport: 1'].odbDisplay.setValues(
    comparisonOdb=odb2,
    comparisonStep='ApplyLoad',
    comparisonFrame=1)
```

---

## D.8 图像和动画输出

### D.8.1 保存图像

```python
# 保存当前视图为图像文件
session.viewports['Viewport: 1'].printToFile(
    fileName='stress_contour.png',
    format=PNG,
    canvasObjects=(session.viewports['Viewport: 1'], ))

# 设置图像分辨率
session.viewports['Viewport: 1'].viewportAnnotationOptions.setValues(
    legendPosition=(50, 50),
    titleBox=ON)
```

### D.8.2 导出动画

```python
# 导出动画为AVI文件
session.viewports['Viewport: 1'].animationController.play(
    duration=5.0,
    timeScale=AUTO)

session.animationController.exportToFile(
    fileName='deformation.avi',
    format=AVI,
    rate=30)
```

---

## D.9 本章小结

本附录介绍了Abaqus/Viewer的主要后处理功能：

1. **变形显示**：查看模型在载荷作用下的变形形状
2. **应力/应变云图**：通过颜色显示结果分布
3. **路径绘图**：沿指定路径提取结果数据
4. **XY曲线**：绘制时间历程曲线和参数关系
5. **报告生成**：输出数值结果到文件
6. **结果比较**：对比不同模型或工况的结果
7. **图像导出**：保存高质量图像和动画

这些工具对于理解和验证有限元分析结果至关重要。

---

*本文档由ABAQUS Getting Started with Abaqus: Interactive Edition (6.14) 翻译生成*
