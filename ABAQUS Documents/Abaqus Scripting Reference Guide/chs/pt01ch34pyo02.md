# 34.4 BeamOrientation 对象

BeamOrientation 对象表示第一个梁截面轴 ![](../graphics/ker_eqn00406.gif) 的方向。不支持使用元素连接列表中的附加节点来指定梁方向。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].beamOrientations[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].beamOrientations[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.beamOrientations[*i*]
```

### 34.4.1 成员

BeamOrientation 对象可以具有以下成员：

*method*

一个 SymbolicConstant，指定方向分配方法。可能的值为 N1_COSINES、CSYS 和 VECT。

*region*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定定义梁方向的区域。

*vector*

浮点数元组，指定梁截面 ![](../graphics/ker_eqn00406.gif) 方向的方向余弦。
