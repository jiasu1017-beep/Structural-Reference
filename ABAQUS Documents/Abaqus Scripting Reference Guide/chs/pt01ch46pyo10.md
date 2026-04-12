# 46.10 GasketSection 对象

GasketSection 对象定义垫片截面的属性。

GasketSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.10.1 GasketSection(...)

此方法创建 GasketSection 对象。

**Path**

```
mdb.models[*name*].GasketSection
session.odbs[*name*].GasketSection
```

**必需参数**

*name*

String，指定存储库键。

*material*

String，指定制造垫片的材料名称或定义垫片行为的材料。

**可选参数**

*crossSection*

Float，指定横截面积、宽度或面外厚度（如果适用），具体取决于垫片单元类型。默认值为 1.0。

*initialGap*

Float，指定初始间隙。默认值为 0.0。

*initialThickness*

SymbolicConstant DEFAULT 或 Float，指定初始垫片厚度。如果指定了 DEFAULT，则使用节点坐标确定初始厚度。默认值为 DEFAULT。

*initialVoid*

Float，指定初始孔隙。默认值为 0.0。

*stabilizationStiffness*

SymbolicConstant DEFAULT 或 Float，指定用于所有链接元素之外的垫片元素的默认稳定刚度，以稳定在所有节点都未支撑的垫片元素，例如延伸出相邻组件的元素。如果指定了 DEFAULT，则使用等于厚度方向初始压缩刚度 10–9 倍的值。默认值为 DEFAULT。

**返回值**

GasketSection 对象。

**异常**

InvalidNameError 和 ValueError。

### 46.10.2 setValues(...)

此方法修改 GasketSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GasketSection](pt01ch46pyo10.md#ker-gasketsection-gasketsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

ValueError。

### 46.10.3 成员

GasketSection 对象的成员与 [GasketSection](pt01ch46pyo10.md#ker-gasketsection-gasketsection-pyc) 方法的参数具有相同的名称和描述。

### 46.10.4 对应分析关键字

| [*GASKET SECTION*](../key/key-link.md#usb-kws-mgasketsection) |
| --- |
