# 29.48 EosCompaction 对象

EosCompaction 对象指定材料压实状态方程。

**访问**

```
import material
mdb.models[*name*].materials[*name*].eos.eosCompaction
import odbMaterial
session.odbs[*name*].materials[*name*].eos.eosCompaction
```

### 29.48.1 EosCompaction(...)

此方法创建 EosCompaction 对象。

**路径**

```
mdb.models[*name*].materials[*name*].eos.EosCompaction
session.odbs[*name*].materials[*name*].eos.EosCompaction
```

**必需参数**

*soundSpeed*

 Float，指定多孔材料中的参考声速。

*porosity*

 Float，指定无载荷材料的孔隙率值。

*pressure*

 Float，指定开始塑性行为所需的压力。

*compactionPressure*

 Float，指定所有孔隙被压碎时的压实压力。

**可选参数**

无。

**返回值**

 EosCompaction 对象。

**异常**

 RangeError。

### 29.48.2 setValues(...)

此方法修改 EosCompaction 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [EosCompaction](pt01ch29pyo48.md#ker-eoscompaction-eoscompaction-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.48.3 成员

EosCompaction 对象的成员与 [EosCompaction](pt01ch29pyo48.md#ker-eoscompaction-eoscompaction-pyc) 方法的参数具有相同的名称和描述。

### 29.48.4 对应的分析关键字

| [*EOS COMPACTION](../key/key-link.md#usb-kws-meoscompaction) |
| --- |
