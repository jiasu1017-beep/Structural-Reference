# 29.99 TriaxialTestData 对象

TriaxialTestData 对象提供三轴测试数据。

**访问**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager.triaxialTestData
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager.triaxialTestData
```

### 29.99.1 TriaxialTestData(...)

此方法创建 TriaxialTestData 对象。

**路径**

```
mdb.models[*name*].materials[*name*].druckerPrager.TriaxialTestData
session.odbs[*name*].materials[*name*].druckerPrager.TriaxialTestData
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*a*

`None` 或 Float，指定材料常数 ![](../graphics/ker_eqn00278.gif) 的值。当值未知或未固定在输入值时使用 `None`。默认值为 `None`。

*b*

`None` 或 Float，指定材料常数 ![](../graphics/ker_eqn00038.gif) 的值。当值未知或未固定在输入值时使用 `None`。默认值为 `None`。

*pt*

`None` 或 Float，指定材料常数 ![](../graphics/ker_eqn00373.gif) 的值。当值未知或未固定在输入值时使用 `None`。默认值为 `None`。

**表格数据**

- 围压的符号和大小，![](../graphics/ker_eqn00374.gif)。
- 加载方向应力的符号和大小，![](../graphics/ker_eqn00375.gif)。

**返回值**

TriaxialTestData 对象。

**异常**

RangeError。

### 29.99.2 setValues(...)

此方法修改 TriaxialTestData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TriaxialTestData](pt01ch29pyo99.md#ker-triaxialtestdata-triaxialtestdata-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.99.3 成员

TriaxialTestData 对象的成员与 [TriaxialTestData](pt01ch29pyo99.md#ker-triaxialtestdata-triaxialtestdata-pyc) 方法的参数具有相同的名称和描述。

### 29.99.4 对应的分析关键字

| [*TRIAXIAL TEST DATA](../key/key-link.md#usb-kws-mtritestdata) |
| --- |
