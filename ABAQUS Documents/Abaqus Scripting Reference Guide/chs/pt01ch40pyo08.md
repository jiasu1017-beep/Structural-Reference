# 40.8 OdbData 对象

OdbData 对象存储给定会话中打开的 odb 的非持久性值和属性。OdbData 对象没有构造函数。导入 Visualization 模块时，Abaqus 创建 *odbData* 存储库。打开 odb 时，Abaqus 创建一个 OdbData 对象。

**访问**

```
import visualization
session.odbData[*name*]
```

### 40.8.1 setValues(...)

此方法修改 OdbData 对象。

**必需参数**

无。

**可选参数**

*activeFrames*

序列，指定活动帧，或 SymbolicConstant ALL。序列中的每个项目是一个元组，定义 stepName，后跟指定帧号的表达式序列。表达式可以是以下任一形式：
- Int，指定单个帧号；例如 `1`。
- String，指定单个帧号；例如 `'7'`。
- String，指定帧号序列；例如 `'3:5'` 和 `'3:15:3'`。

 对于这些表达式，负数表示反向编号：-1 是步骤的最后一帧，-2 是倒数第二帧。帧编号从 0 开始。

*stepPeriods*

 (String, Float) 序列的序列，指定 stepName 和 stepPeriod。或者，此成员可以取 ODB_VALUES 值。

**返回值**

无

**异常**

无。

### 40.8.2 成员

OdbData 对象可以具有以下成员：

*activeFrames*

元组，指定活动帧，或 SymbolicConstant ALL。序列中的每个项目是一个元组，定义 stepName，后跟指定帧号的表达式序列。表达式可以是以下任一形式：
- Int，指定单个帧号；例如 `1`。
- String，指定单个帧号；例如 `'7'`。
- String，指定帧号序列；例如 `'3:5'` 和 `'3:15:3'`。

 对于这些表达式，负数表示反向编号：-1 是步骤的最后一帧，-2 是倒数第二帧。帧编号从 0 开始。

*stepPeriods*

 (String, Float) 元组的元组，指定 stepName 和 stepPeriod。或者，此成员可以取 ODB_VALUES 值。

*historyVariables*

 [HistoryVariable](pt01ch40pyo07.md) 对象存储库，指定历史请求标签。此存储库为只读。

*steps*

 [OdbDataStep](pt01ch40pyo16.md) 对象存储库，指定步骤列表。此存储库为只读。

*instances*

 [OdbDataInstance](pt01ch40pyo12.md) 对象存储库，指定实例列表。此存储库为只读。

*materials*

 [OdbDataMaterial](pt01ch40pyo13.md) 对象存储库，指定材料列表。此存储库为只读。

*sections*

 [OdbDataSection](pt01ch40pyo15.md) 对象存储库，指定截面列表。此存储库为只读。

*elementSets*

 [OdbDataElementSet](pt01ch40pyo10.md) 对象存储库，指定单元集列表。此存储库为只读。

*nodeSets*

 [OdbDataNodeSet](pt01ch40pyo14.md) 对象存储库，指定节点集列表。此存储库为只读。

*surfaceSets*

 [OdbDataSurfaceSet](pt01ch40pyo17.md) 对象存储库，指定曲面集列表。此存储库为只读。

*datumCsyses*

 [OdbDataDatumCsys](pt01ch40pyo09.md) 对象存储库，指定模型中定义的坐标系列表。此存储库为只读。

