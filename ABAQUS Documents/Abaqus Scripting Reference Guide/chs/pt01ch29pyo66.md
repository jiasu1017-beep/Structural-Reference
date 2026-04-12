# 29.66 LatentHeat 对象

LatentHeat 对象指定材料的潜热。

**访问**

```
import material
mdb.models[*name*].materials[*name*].latentHeat
import odbMaterial
session.odbs[*name*].materials[*name*].latentHeat
```

### 29.66.1 LatentHeat(...)

此方法创建 LatentHeat 对象。

**路径**

```
mdb.models[*name*].materials[*name*].LatentHeat
session.odbs[*name*].materials[*name*].LatentHeat
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

无。

**表格数据**

- 单位质量的潜热。
- 固相线温度。
- 液相线温度。

**返回值**

LatentHeat 对象。

**异常**

RangeError。

### 29.66.2 setValues(...)

此方法修改 LatentHeat 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [LatentHeat](pt01ch29pyo66.md#ker-latentheat-latentheat-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.66.3 成员

LatentHeat 对象的成员与 [LatentHeat](pt01ch29pyo66.md#ker-latentheat-latentheat-pyc) 方法的参数具有相同的名称和描述。

### 29.66.4 对应的分析关键字

| [*LATENT HEAT](../key/key-link.md#usb-kws-mlatentheat) |
| --- |
