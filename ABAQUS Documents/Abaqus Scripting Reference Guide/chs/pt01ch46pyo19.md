# 46.19 RebarLayers 对象

RebarLayers 对象定义截面的钢筋属性。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.rebarLayers
mdb.models[*name*].sections[*name*].rebarLayers
import odbSection
session.odbs[*name*].sections[*name*].rebarLayers
```

### 46.19.1 RebarLayers(...)

此方法创建 RebarLayers 对象。

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.RebarLayers
mdb.models[*name*].sections[*name*].RebarLayers
session.odbs[*name*].sections[*name*].RebarLayers
```

**必需参数**

*rebarSpacing*

SymbolicConstant，指定钢筋几何形状的类型。可选值为 CONSTANT、ANGULAR 和 LIFT_EQUATION。

*layerTable*

[LayerPropertiesArray](pt01ch46pyo15.md) 对象，指定增强层。

**可选参数**

无。

**返回值**

RebarLayers 对象。

**异常**

无。

### 46.19.2 setValues(...)

此方法修改 RebarLayers 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RebarLayers](pt01ch46pyo19.md#ker-rebarlayers-rebarlayers-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 46.19.3 成员

RebarLayers 对象的成员与 [RebarLayers](pt01ch46pyo19.md#ker-rebarlayers-rebarlayers-pyc) 方法的参数具有相同的名称和描述。

### 46.19.4 对应分析关键字

| [*REBAR LAYER*](../key/key-link.md#usb-kws-mrebarlayer) |
| --- |
