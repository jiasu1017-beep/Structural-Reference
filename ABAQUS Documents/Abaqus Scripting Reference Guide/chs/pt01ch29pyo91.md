# 29.91 SimpleShearTestData 对象

SimpleShearTestData 对象提供简单剪切测试数据。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperfoam.simpleShearTestData
import odbMaterial
session.odbs[*name*].materials[*name*].hyperfoam.simpleShearTestData
```

### 29.91.1 SimpleShearTestData(...)

此方法创建 SimpleShearTestData 对象。

**路径**

```
mdb.models[*name*].materials[*name*].hyperfoam.SimpleShearTestData
session.odbs[*name*].materials[*name*].hyperfoam.SimpleShearTestData
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

无。

**表格数据**

- 名义剪切应力，![](../graphics/ker_eqn00332.gif)。
- 名义剪切应变，![](../graphics/ker_eqn00040.gif)。
- 名义横向应力，![](../graphics/ker_eqn00366.gif)（垂直于剪切应力边缘）。此应力值是可选的。

**返回值**

SimpleShearTestData 对象。

**异常**

无。

### 29.91.2 setValues(...)

此方法修改 SimpleShearTestData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SimpleShearTestData](pt01ch29pyo91.md#ker-simplesheartestdata-simplesheartestdata-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.91.3 成员

SimpleShearTestData 对象的成员与 [SimpleShearTestData](pt01ch29pyo91.md#ker-simplesheartestdata-simplesheartestdata-pyc) 方法的参数具有相同的名称和描述。

### 29.91.4 对应的分析关键字

| [*SIMPLE SHEAR TEST DATA](../key/key-link.md#usb-kws-msimplesheartestdata) |
| --- |
