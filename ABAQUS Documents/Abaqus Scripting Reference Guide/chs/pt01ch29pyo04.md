# 29.4 BiaxialTestData 对象





BiaxialTestData 对象提供等双轴测试数据（压缩和/或拉伸）。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.biaxialTestData
mdb.models[*name*].materials[*name*].hyperfoam.biaxialTestData
mdb.models[*name*].materials[*name*].mullinsEffect.biaxialTests[*i*]
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.biaxialTestData
session.odbs[*name*].materials[*name*].hyperfoam.biaxialTestData
session.odbs[*name*].materials[*name*].mullinsEffect.biaxialTests[*i*]
```

### 29.4.1 BiaxialTestData(...)

此方法创建 BiaxialTestData 对象。

**路径**

```
mdb.models[*name*].materials[*name*].hyperelastic.BiaxialTestData
mdb.models[*name*].materials[*name*].hyperfoam.BiaxialTestData
mdb.models[*name*].materials[*name*].mullinsEffect.BiaxialTestData
session.odbs[*name*].materials[*name*].hyperelastic.BiaxialTestData
session.odbs[*name*].materials[*name*].hyperfoam.BiaxialTestData
session.odbs[*name*].materials[*name*].mullinsEffect.BiaxialTestData
```

**必需参数**

*table*

一个 Float 序列的序列，指定以下内容：
- 名义应力，![](../graphics/ker_eqn00086.gif)。
- 名义应变，![](../graphics/ker_eqn00087.gif)。

**可选参数**

*smoothing*

`None` 或一个 Int，指定平滑值。如果 *smoothing*=`None`，则不进行平滑处理。默认值为 `None`。

*lateralNominalStrain*

一个 Boolean，指定是否包含横向名义应变。默认值为 OFF。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**返回值**

一个 BiaxialTestData 对象。

**异常**

无。

### 29.4.2 setValues(...)

此方法修改 BiaxialTestData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BiaxialTestData](pt01ch29pyo04.md#ker-biaxialtestdata-biaxialtestdata-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.4.3 成员

BiaxialTestData 对象具有与 [BiaxialTestData](pt01ch29pyo04.md#ker-biaxialtestdata-biaxialtestdata-pyc) 方法参数同名的成员，描述也相同。

### 29.4.4 对应的分析关键字

| [*BIAXIAL TEST DATA](../key/key-link.md#usb-kws-mbitestdata) |
| --- |




