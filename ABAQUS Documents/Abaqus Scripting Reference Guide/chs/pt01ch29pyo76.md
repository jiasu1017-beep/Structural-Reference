# 29.76 PlanarTestData 对象

PlanarTestData 对象指定平面测试（或纯剪切）数据（压缩和/或拉伸）。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.planarTestData
mdb.models[*name*].materials[*name*].hyperfoam.planarTestData
mdb.models[*name*].materials[*name*].mullinsEffect.planarTests[*i*]
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.planarTestData
session.odbs[*name*].materials[*name*].hyperfoam.planarTestData
session.odbs[*name*].materials[*name*].mullinsEffect.planarTests[*i*]
```

### 29.76.1 PlanarTestData(...)

此方法创建 PlanarTestData 对象。

**路径**

```
mdb.models[*name*].materials[*name*].hyperelastic.PlanarTestData
mdb.models[*name*].materials[*name*].hyperfoam.PlanarTestData
mdb.models[*name*].materials[*name*].mullinsEffect.PlanarTestData
session.odbs[*name*].materials[*name*].hyperelastic.PlanarTestData
session.odbs[*name*].materials[*name*].hyperfoam.PlanarTestData
session.odbs[*name*].materials[*name*].mullinsEffect.PlanarTestData
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*smoothing*

`None` 或 Int，指定平滑值。如果 *smoothing*=`None`，则不使用平滑。默认值为 `None`。

*lateralNominalStrain*

Boolean，指定是否包含横向名义应变。默认值为 OFF。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

对于超弹性材料模型，表格数据指定以下内容：
- 名义应力，![](../graphics/ker_eqn00332.gif)。
- 加载方向的名义应变，![](../graphics/ker_eqn00333.gif)。

对于超泡沫材料模型，表格数据指定以下内容：
- 名义应力，![](../graphics/ker_eqn00334.gif)。
- 加载方向的名义应变，![](../graphics/ker_eqn00335.gif)。
- 横向名义应变，![](../graphics/ker_eqn00336.gif)。默认值为 0。

**返回值**

PlanarTestData 对象。

**异常**

无。

### 29.76.2 setValues(...)

此方法修改 PlanarTestData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PlanarTestData](pt01ch29pyo76.md#ker-planartestdata-planartestdata-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.76.3 成员

PlanarTestData 对象的成员与 [PlanarTestData](pt01ch29pyo76.md#ker-planartestdata-planartestdata-pyc) 方法的参数具有相同的名称和描述。

### 29.76.4 对应的分析关键字

| [*PLANAR TEST DATA](../key/key-link.md#usb-kws-mplanartestdata) |
| --- |
