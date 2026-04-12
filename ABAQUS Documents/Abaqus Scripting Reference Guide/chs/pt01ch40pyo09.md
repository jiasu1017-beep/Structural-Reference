# 40.9 OdbDataDatumCsys 对象

OdbDataDatumCsys 对象存储坐标系数据。

**访问**

```
import visualization
session.odbData[*name*].datumCsyses[*i*]
```

### 40.9.1 成员

OdbDataDatumCsys 对象可以具有以下成员：

*name*

 String，指定坐标系名称。此字符串为只读。

*type*

 SymbolicConstant，指定坐标系类型。此字符串为只读。可选值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*xAxis*

三个 Float 的元组，指定三个浮点数指定 x 轴向量。默认值为 (1, 0, 0)。

*yAxis*

三个 Float 的元组，指定三个浮点数指定 y 轴向量。默认值为 (0, 1, 0)。

*zAxis*

三个 Float 的元组，指定三个浮点数指定 z 轴向量。默认值为 (0, 0, 1)。

*origin*

三个 Float 的元组，指定三个浮点数指定原点。默认值为 (0, 0, 0)。

