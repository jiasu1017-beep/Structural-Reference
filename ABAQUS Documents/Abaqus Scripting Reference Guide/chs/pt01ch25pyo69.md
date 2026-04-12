# 25.69 StdXplCosimulation 对象

StdXplCosimulation 对象定义 Abaqus/Standard 和 Abaqus/Explicit 之间的协同仿真行为。

StdXplCosimulation 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.69.1 StdXplCosimulation(...)

此方法创建一个 StdXplCosimulation 对象。

**路径**

```
mdb.models[*name*].StdXplCosimulation
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 StdXplCosimulation 对象的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定协同仿真与耦合分析程序交换数据的导入和导出区域。

**可选参数**

*incrementation*

 SymbolicConstant，指定分析程序使用相同的时间增量，还是允许其中一个在使用的数据之前使用更多时间增量。可能的值为 ALLOW_SUBCYCLING 和 LOCKSTEP。默认值为 ALLOW_SUBCYCLING。

*stepSize*

浮点数，指定用于 Abaqus/Standard 和 Abaqus/Explicit 的增量大小。默认值为 0.0。

*stepSizeDefinition*

 SymbolicConstant，指定增量大小是分析默认值还是提供的变量。可能的值为 DEFAULT 和 SPECIFIED。默认值为 DEFAULT