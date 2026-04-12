# 46.9 EulerianSection 对象

EulerianSection 对象定义欧拉截面的属性。

EulerianSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.9.1 EulerianSection(...)

此方法创建 EulerianSection 对象。

**Path**

```
mdb.models[*name*].EulerianSection
session.odbs[*name*].EulerianSection
```

**必需参数**

*name*

String，指定存储库键。

*data*

String-to-String Dictionary，指定将材料实例名称映射到材料名称的字典。内部指定的映射按材料实例名称排序。

**可选参数**

无。

**返回值**

EulerianSection 对象。

**异常**

无。

### 46.9.2 setValues(...)

此方法修改 EulerianSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [EulerianSection](pt01ch46pyo09.md#ker-euleriansection-euleriansection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 46.9.3 成员

EulerianSection 对象的成员与 [EulerianSection](pt01ch46pyo09.md#ker-euleriansection-euleriansection-pyc) 方法的参数具有相同的名称和描述。

### 46.9.4 对应分析关键字

| [*EULERIAN SECTION*](../key/key-link.md#usb-kws-meulsection) |
| --- |
