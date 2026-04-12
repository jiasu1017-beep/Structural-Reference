# 29.56 GasketThicknessBehavior 对象

GasketThicknessBehavior 对象定义垫片厚度方向的行为。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gasketThicknessBehavior
import odbMaterial
session.odbs[*name*].materials[*name*].gasketThicknessBehavior
```

### 29.56.1 GasketThicknessBehavior(...)

此方法创建 GasketThicknessBehavior 对象。

**路径**

```
mdb.models[*name*].materials[*name*].GasketThicknessBehavior
session.odbs[*name*].materials[*name*].GasketThicknessBehavior
```

**必需参数**

*table*

 Float 元组序列，指定加载数据。第一个序列必须仅包含 0。如果 *type*=DAMAGE，则至少需要两个序列；如果 *type*=ELASTIC_PLASTIC，则至少需要三个序列。表格数据中的项目如下所述。

**可选参数**

*temperatureDependency*

 Boolean，指定加载数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定加载数据定义中除温度外的场变量依赖项数量。默认值为 0。

*tensileStiffnessFactor*

 Float，指定初始压缩刚度的分数，定义拉伸刚度。默认值为 10–3。

*type*

 SymbolicConstant，指定垫片厚度方向行为的损伤弹性模型或弹塑性模型。可能的值为 ELASTIC_PLASTIC 和 DAMAGE。默认值为 ELASTIC_PLASTIC。

*unloadingDependencies*

 Int，指定卸载数据定义中除温度外的场变量依赖项数量。默认值为 0。

*unloadingTemperatureDependency*

 Boolean，指定卸载数据是否依赖于温度。默认值为 OFF。

*variableUnits*

 SymbolicConstant，指定以力（或单位长度力）与闭合的关系或压力与闭合的关系表示的行为。可能的值为 STRESS 和 FORCE。默认值为 STRESS。

*yieldOnset*

 Float，指定发生屈服的闭合值，或定义塑性变形开始时加载曲线上相对斜率下降的闭合值（取决于 *yieldOnsetMethod* 的值）。默认值为 0.1。

*yieldOnsetMethod*

 SymbolicConstant，指定确定屈服开始的方法。可能的值为 RELATIVE_SLOPE_DROP 和 CLOSURE_VALUE。默认值为 RELATIVE_SLOPE_DROP。

*unloadingTable*

 Float 元组序列，指定卸载数据。表格数据中的项目如下所述。默认值为空序列。

**表格数据**

如果 *variableUnits*=STRESS，加载表格数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *variableUnits*=FORCE，加载表格数据指定以下内容：
- 力或单位长度力；此值必须为正。
- 闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *variableUnits*=STRESS 且 *type*=ELASTIC_PLASTIC，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 塑性闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *variableUnits*=FORCE 且 *type*=ELASTIC_PLASTIC，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 塑性闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *variableUnits*=STRESS 且 *type*=DAMAGE，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 加载垫片时达到的最大闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *variableUnits*=FORCE 且 *type*=DAMAGE，*unloadingTable* 数据指定以下内容：
- 力或单位长度力；此值必须为正。
- 闭合；此值必须为正。
- 加载垫片时达到的最大闭合；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 GasketThicknessBehavior 对象。

**异常**

 RangeError。

### 29.56.2 setValues(...)

此方法修改 GasketThicknessBehavior 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [GasketThicknessBehavior](pt01ch29pyo56.md#ker-gasketthicknessbehavior-gasketthicknessbehavior-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.56.3 成员

GasketThicknessBehavior 对象的成员与 [GasketThicknessBehavior](pt01ch29pyo56.md#ker-gasketthicknessbehavior-gasketthicknessbehavior-pyc) 方法的参数具有相同的名称和描述。

此外，GasketThicknessBehavior 对象可以具有以下成员：

*contactArea*

 [ContactArea](pt01ch29pyo25.md) 对象。

### 29.56.4 对应的分析关键字

| [*GASKET THICKNESS BEHAVIOR](../key/key-link.md#usb-kws-mgasketnormal) |
| --- |
