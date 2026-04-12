# 34.13 OdbDatumCsys 对象

OdbDatumCsys 对象包含可以存储在输出数据库中的坐标系。您可以在 Abaqus/CAE 会话期间在 Visualization 模块中创建基准坐标系，并在退出 Abaqus/CAE 之前将基准坐标系保存到输出数据库。或者，分析代码可以将基准坐标系写入输出数据库。

**访问**

```
import odbAccess
session.odbs[*name*].rootAssembly.datumCsyses[*name*]
```

### 34.13.1 DatumCsysByThreePoints(...)

此方法使用三个点创建 OdbDatumCsys 对象。使用此方法创建的基准坐标系会生成一个固定系统。

**路径**

```
session.odbs[*name*].rootAssembly.DatumCsysByThreePoints
```

**必要参数**

*name*

一个字符串，指定仓库键。

*coordSysType*

一个 SymbolicConstant，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*origin*

浮点数序列，指定基准坐标系原点的坐标。

*point1*

浮点数序列，指定局部 1 轴或 ![](../graphics/ker_eqn00052.gif) 轴上一点的坐标。

*point2*

浮点数序列，指定 1-2 或 ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) 平面中一点的坐标。

**可选参数**

无。

**返回值**

OdbDatumCsys 对象。

**异常**

无。

### 34.13.2 DatumCsysByThreeNodes(...)

此方法使用三个 [OdbMeshNode](pt01ch34pyo18.md) 对象的坐标创建 OdbDatumCsys 对象。使用此方法创建的基准坐标系会生成一个跟随三个节点位置的系统。结果（如位移）被分解为基准坐标系的方向，而不考虑其原点的位置。最后三个参数以 [OdbMeshNode](pt01ch34pyo18.md) 对象的形式给出。

**路径**

```
session.odbs[*name*].rootAssembly.DatumCsysByThreeNodes
```

**必要参数**

*name*

一个字符串，指定仓库键。

*coordSysType*

一个 SymbolicConstant，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*origin*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定基准坐标系原点处的节点。

*point1*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定局部 1 轴或 ![](../graphics/ker_eqn00052.gif) 轴上的节点。

*point2*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定 1-2 或 ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) 平面中的节点。

**可选参数**

无。

**返回值**

OdbDatumCsys 对象。

**异常**

无。

### 34.13.3 DatumCsysByThreeCircNodes(...)

此方法在没有沿空心圆柱轴向的节点或空心球体中心的节点时使用很方便。您作为参数提供的三个节点在空间中确定一个圆。圆的中心是基准坐标系的原点。圆的法线平行于圆柱坐标系的 ![](../graphics/ker_eqn00055.gif) 轴或球坐标系的 ![](../graphics/ker_eqn00291.gif) 轴。从原点到第一个节点的连线定义 ![](../graphics/ker_eqn00052.gif) 轴。

**路径**

```
session.odbs[*name*].rootAssembly.DatumCsysByThreeCircNodes
```

**必要参数**

*name*

一个字符串，指定仓库键。

*coordSysType*

一个 SymbolicConstant，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*node1Arc*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，位于圆弧上。

*node2Arc*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，位于圆弧上。

*node3Arc*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，位于圆弧上。

**可选参数**

无。

**返回值**

OdbDatumCsys 对象。

**异常**

无。

### 34.13.4 DatumCsysBy6dofNode(...)

使用此方法创建的基准坐标系会生成一个跟随节点位置的系统。节点位置定义基准坐标系的原点。节点的旋转位移（UR1、UR2、UR3）定义坐标系轴的方向。结果（如位移）被分解为基准坐标系的方向，而不考虑其原点的位置。最后一个参数以 [OdbMeshNode](pt01ch34pyo18.md) 对象的形式给出。

**路径**

```
session.odbs[*name*].rootAssembly.DatumCsysBy6dofNode
```

**必要参数**

*name*

一个字符串，指定仓库键。

*coordSysType*

一个 SymbolicConstant，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*origin*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定基准坐标系的原点。

**可选参数**

无。

**返回值**

OdbDatumCsys 对象。

**异常**

无。

### 34.13.5 DatumCsys(...)

此方法将一个 OdbDatumCsys 对象复制到一个新的 OdbDatumCsys 对象。

**路径**

```
session.odbs[*name*].rootAssembly.DatumCsys
```

**必要参数**

*name*

一个字符串，指定仓库键。

*datumCsys*

一个 OdbDatumCsys 对象，指定要复制的对象。

**可选参数**

无。

**返回值**

OdbDatumCsys 对象。

**异常**

无。

### 34.13.6 成员

OdbDatumCsys 对象具有以下成员：

*name*

一个字符串，指定仓库键。

*coordSysType*

一个 SymbolicConstant，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*origin*

浮点数元组，指定基准坐标系原点的坐标。

*xAxis*

浮点数元组，指定 *X* 轴上的一点。

*yAxis*

浮点数元组，指定 *Y* 轴上的一点。

*zAxis*

浮点数元组，指定 *Z* 轴上的一点。
