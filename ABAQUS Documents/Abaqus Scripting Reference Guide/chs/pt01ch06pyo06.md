# 6.6 Model 对象





以下命令对 Model 对象进行操作。有关 Model 对象的更多信息，请参见["Model 对象"，第 33.1 节](pt01ch33pyo01.md)。

**访问**

```
import assembly
```

### 6.6.1 Instance(...)

此方法从指定模型复制 [PartInstance](pt01ch06pyo04.md) 对象，并创建一个新的 [PartInstance](pt01ch06pyo04.md) 对象。

**路径**

```
mdb.models[*name*].Instance
```

**必需参数**

*name*

一个 String，指定仓库键。

*objectToCopy*

一个 [PartInstance](pt01ch06pyo04.md) 对象要被复制。

**可选参数**

无。

**返回值**

一个 Model 对象。

**异常**

无。

### 6.6.2 convertAllSketches(...)

此方法将所有草图从 Abaqus 6.5 或更早版本转换为等效的 [ConstrainedSketch](pt01ch48pyo01.md) 对象。

**必需参数**

无。

**可选参数**

*regenerate*

一个 Boolean，指定在转换后是否应重新生成装配以及模型中所有零件中的所有特征。默认值为 True。

*convertReversedSketches*

一个 Boolean，指定即使草图导致在其上定义的表面方向翻转，是否也应转换分析刚性零件中的草图。默认值为 True。

**返回值**

一个字符串列表，描述转换过程中遇到的任何警告或错误。

**异常**

无。

### 6.6.3 linkInstances(...)

此方法将所选的 [PartInstance](pt01ch06pyo04.md) 对象链接到指定模型中的相应 [PartInstance](pt01ch06pyo04.md) 对象。如果选择了零件的所有实例进行链接，则该零件也将被链接。否则，将创建一个新的链接子 Part 对象并添加到仓库。

**必需参数**

*instancesMap*

一个元组元组，包含要链接的实例名称和对应的 [PartInstance](pt01ch06pyo04.md) 对象。

**可选参数**

无。

**返回值**

一个字符串列表，描述转换过程中遇到的任何警告或错误。

**异常**

无。




