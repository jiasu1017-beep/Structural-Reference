# 29.72 MullinsEffect 对象

MullinsEffect 指定 Mullins 数据的属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].mullinsEffect
import odbMaterial
session.odbs[*name*].materials[*name*].mullinsEffect
```

### 29.72.1 成员

MullinsEffect 对象可以具有以下成员：

*definition*

SymbolicConstant，指定指定数据的方法。可能的值为 USER、CONSTANTS 和 TEST_DATA。默认值为 CONSTANTS。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

*properties*

Int，指定作为用户定义超弹性材料数据所需的属性值数量。默认值为 0。

*table*

Float 元组序列，指定下述项目。默认值为空序列。

*uniaxialTests*

[UniaxialTestDataArray](pt01ch29pyo101.md) 对象。

*biaxialTests*

[BiaxialTestDataArray](pt01ch29pyo04.md) 对象。

*planarTests*

[PlanarTestDataArray](pt01ch29pyo76.md) 对象。
