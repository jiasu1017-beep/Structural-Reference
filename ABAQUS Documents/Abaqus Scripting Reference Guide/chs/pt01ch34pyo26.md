# 34.25 RebarOrientation 对象

RebarOrientation 对象表示钢筋参考的方向。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].rebarOrientations[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].rebarOrientations[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.rebarOrientations[*i*]
```

### 34.25.1 成员

RebarOrientation 对象可以具有以下成员：

*axis*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用额外旋转。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。

*angle*

一个 Float，指定额外旋转的角度。

*region*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定定义钢筋方向区域。

*csys*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定基准坐标系。
