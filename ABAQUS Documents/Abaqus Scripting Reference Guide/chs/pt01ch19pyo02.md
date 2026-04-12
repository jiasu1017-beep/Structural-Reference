# 19.2 AssembledFastener 对象









AssembledFastener 对象定义装配紧固件。

AssembledFastener 对象派生自 [Fastener](pt01ch19pyo07.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.2.1 AssembledFastener(...)

此方法创建 AssembledFastener 对象。尽管构造函数可用于部件和装配，但 AssembledFastener 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.AssembledFastener
mdb.models[*name*].rootAssembly.engineeringFeatures.AssembledFastener
```

**必需参数**

*name*

一个 String，指定存储库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用装配紧固件的附着点区域。

*templateModel*

一个 String，指定模板模型的名称。

*controlSet*

一个 [Region](pt01ch45pyo03.md) 对象，指定模板模型控制点集。该集必须包含单个节点或顶点。

*templateSurfaces*

一个 String 序列，指定由绑定或耦合约束引用的模板模型表面的名称。

*assignedSurfaces*

一个 String 序列，指定将替换模板模型约束表面的主模型表面的名称。

*propertyPrefix*

一个 String，指定属性前缀字符串的名称。此字符串在从模板模型复制到主模型时将被预先挂载到每个属性名称。

**可选参数**

*orientMethod*

一个 SymbolicConstant，指定在每个附着点处定向模板模型虚拟实例的方法。可能的值为 NORMALS 和 CSYS。默认值为 NORMALS。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系。如果 *localCsys*=`None`，则使用全局坐标系。查询此成员时，它返回一个 Int。默认值为 `None`。

此参数仅在 *orientMethod*=CSYS 时适用。

*scriptName*

一个 String，指定属性生成脚本的名称。默认值为空字符串。

**返回值**

一个 AssembledFastener 对象。

**异常**

无。

### 19.2.2 setValues(...)

此方法修改 AssembledFastener 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AssembledFastener](pt01ch19pyo02.md#ker-assembledfastener-assembledfastener-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.2.3 成员

AssembledFastener 对象具有与 [AssembledFastener](pt01ch19pyo02.md#ker-assembledfastener-assembledfastener-pyc) 方法的参数相同的名称和描述的成员。

此外，AssembledFastener 对象还有以下成员：

*suppressed*

一个 Boolean，指定紧固件是否被抑制。默认值为 OFF。





