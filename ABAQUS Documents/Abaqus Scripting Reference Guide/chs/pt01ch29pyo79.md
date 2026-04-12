# 29.79 PorousBulkModuli 对象

PorousBulkModuli 对象定义土壤和岩石的体积模量。

**访问**

```
import material
mdb.models[*name*].materials[*name*].porousBulkModuli
import odbMaterial
session.odbs[*name*].materials[*name*].porousBulkModuli
```

### 29.79.1 PorousBulkModuli(...)

此方法创建 PorousBulkModuli 对象。

**路径**

```
mdb.models[*name*].materials[*name*].PorousBulkModuli
session.odbs[*name*].materials[*name*].PorousBulkModuli
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

**表格数据**

- 固体颗粒的体积模量。
- 渗透流体的体积模量。
- 温度（如果数据依赖于温度）。

**返回值**

PorousBulkModuli 对象。

**异常**

无。

### 29.79.2 setValues(...)

此方法修改 PorousBulkModuli 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PorousBulkModuli](pt01ch29pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.79.3 成员

PorousBulkModuli 对象的成员与 [PorousBulkModuli](pt01ch29pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-pyc) 方法的参数具有相同的名称和描述。

### 29.79.4 对应的分析关键字

| [*POROUS BULK MODULI](../key/key-link.md#usb-kws-mporousbulkmod) |
| --- |
