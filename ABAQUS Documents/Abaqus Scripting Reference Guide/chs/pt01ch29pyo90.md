# 29.90 ShearTestData 对象

ShearTestData 对象将归一化剪切蠕变柔量或松弛模量指定为时间的函数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].viscoelastic.shearTestData
import odbMaterial
session.odbs[*name*].materials[*name*].viscoelastic.shearTestData
```

### 29.90.1 ShearTestData(...)

此方法创建 ShearTestData 对象。

**路径**

```
mdb.models[*name*].materials[*name*].viscoelastic.ShearTestData
session.odbs[*name*].materials[*name*].viscoelastic.ShearTestData
```

**必需参数**

*table*

Float 元组序列，指定依赖于 [Viscoelastic](pt01ch29pyo106.md) 对象的 *time* 成员的值。

如果 *time*=RELAXATION_TEST_DATA，表格数据指定以下内容：
- 归一化剪切松弛模量 ![](../graphics/ker_eqn00117.gif)。![](../graphics/ker_eqn00118.gif)。
- 时间 ![](../graphics/ker_eqn00093.gif)。![](../graphics/ker_eqn00121.gif)。

如果 *time*=CREEP_TEST_DATA，表格数据指定以下内容：
- 归一化剪切柔量 ![](../graphics/ker_eqn00122.gif)。![](../graphics/ker_eqn00365.gif)。
- 时间 ![](../graphics/ker_eqn00093.gif)。![](../graphics/ker_eqn00121.gif)。

**可选参数**

*shrinf*

`None` 或 Float，指定归一化剪切。*shrinf* 的值取决于 [Viscoelastic](pt01ch29pyo106.md) 对象的 *time* 成员的值。默认值为 `None`。

如果 *time*=RELAXATION_TEST_DATA，*shrinf* 指定长期归一化剪切模量 ![](../graphics/ker_eqn00115.gif) 的值。

如果 *time*=CREEP_TEST_DATA，*shrinf* 指定长期归一化剪切柔量 ![](../graphics/ker_eqn00116.gif) 的值。

**返回值**

ShearTestData 对象。

**异常**

无。

### 29.90.2 setValues(...)

此方法修改 ShearTestData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShearTestData](pt01ch29pyo90.md#ker-sheartestdata-sheartestdata-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.90.3 成员

ShearTestData 对象的成员与 [ShearTestData](pt01ch29pyo90.md#ker-sheartestdata-sheartestdata-pyc) 方法的参数具有相同的名称和描述。

### 29.90.4 对应的分析关键字

| [*SHEAR TEST DATA](../key/key-link.md#usb-kws-msheartestdata) |
| --- |
