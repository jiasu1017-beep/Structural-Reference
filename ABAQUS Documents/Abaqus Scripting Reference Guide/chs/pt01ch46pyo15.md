# 46.15 LayerProperties 对象

LayerProperties 对象定义膜、壳和表面截面增强层属性。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.rebarLayers.layerTable[*i*]
mdb.models[*name*].sections[*name*].rebarLayers.layerTable[*i*]
import odbSection
session.odbs[*name*].sections[*name*].rebarLayers.layerTable[*i*]
```

### 46.15.1 LayerProperties(...)

此方法创建 LayerProperties 对象。

**Path**

```
section.LayerProperties
```

```
odbSection.LayerProperties
```

**必需参数**

*barArea*

Float，指定每根钢筋的面积。

*orientationAngle*

Float 或 String，指定钢筋的方向。Float 指定角度方向；String 指定方向名称。

*layerName*

String，指定钢筋层的名称。

*material*

String，指定钢筋材料的名称。

**可选参数**

*barSpacing*

Float，指定钢筋的间距。此参数仅在父 [RebarLayers](pt01ch46pyo19.md) 对象的 *rebarSpacing* 参数设置为 CONSTANT 时有效。默认值为 0.0。

*layerPosition*

Float，指定钢筋从壳中面算起的位置。*layerPosition* 仅适用于均匀壳截面和复合壳截面。默认值为 0.0。

*spacingAngle*

Float，指定钢筋的间距角度。此参数仅在父 [RebarLayers](pt01ch46pyo19.md) 对象的 *rebarSpacing* 参数设置为 ANGULAR 时有效。默认值为 0.0。

*extensionRatio*

Float，指定钢筋的延伸比。此参数仅在父 [RebarLayers](pt01ch46pyo19.md) 对象的 *rebarSpacing* 参数设置为 LIFT_EQUATION 时有效。默认值为 0.0。

*radius*

Float，指定钢筋的半径。此参数仅在父 [RebarLayers](pt01ch46pyo19.md) 对象的 *rebarSpacing* 参数设置为 LIFT_EQUATION 时有效。默认值为 0.0。

**返回值**

LayerProperties 对象。

**异常**

无。

### 46.15.2 成员

LayerProperties 对象的成员与 [LayerProperties](pt01ch46pyo15.md#ker-layerproperties-layerproperties-pyc) 方法的参数具有相同的名称和描述。

### 46.15.3 对应分析关键字

| [*REBAR LAYER*](../key/key-link.md#usb-kws-mrebarlayer) |
| --- |
