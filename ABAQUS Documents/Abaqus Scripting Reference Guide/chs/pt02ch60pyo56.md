# 60.56 GasketThicknessBehavior 对象

GasketThicknessBehavior 对象用于定义垫片厚度方向的行为。

**访问**

```
materialApi.materials()[*name*].gasketThicknessBehavior()
```

### 60.56.1 GasketThicknessBehavior(...)

此方法创建一个 GasketThicknessBehavior 对象。

**路径**

```
materialApi.materials()[*name*].GasketThicknessBehavior
```

**原型**

```
odb_GasketThicknessBehavior&
GasketThicknessBehavior(const odb_SequenceSequenceDouble& table,
            bool temperatureDependency,
            int dependencies,
            double tensileStiffnessFactor,
            const odb_String& type,
            int unloadingDependencies,
            bool unloadingTemperatureDependency,
            const odb_String& variableUnits,
            double yieldOnset,
            const odb_String& yieldOnsetMethod,
            const odb_SequenceSequenceDouble& unloadingTable);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定加载数据。第一个序列必须仅包含 0。如果 *type*="DAMAGE"，则必须至少指定两个序列；如果 *type*="ELASTIC_PLASTIC"，则必须至少指定三个序列。表数据中的项目如下所述。

**可选参数**

*temperatureDependency*

一个布尔值，指定加载数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定除温度外还包括在加载数据定义中的场变量依赖数量。默认值为 0。

*tensileStiffnessFactor*

一个 Double，指定初始压缩刚度的分数，定义为拉伸刚度。默认值为 10–3。

*type*

一个 odb_String，指定垫片厚度方向行为的损伤弹性模型或弹塑性模型。可能的值为"ELASTIC_PLASTIC"和"DAMAGE"。默认值为"ELASTIC_PLASTIC"。

*unloadingDependencies*

一个整数，指定除温度外还包括在卸载数据定义中的场变量依赖数量。默认值为 0。

*unloadingTemperatureDependency*

一个布尔值，指定卸载数据是否依赖温度。默认值为 false。

*variableUnits*

一个 odb_String，指定以力（或单位长度上的力）与闭合的关系或压力与闭合的关系表示的行为。可能的值为"STRESS"和"FORCE"。默认值为"STRESS"。

*yieldOnset*

一个 Double，指定发生屈服的闭合值，或定义塑性变形开始时加载曲线上相对斜率下降的值（取决于 *yieldOnsetMethod* 的值）。默认值为 0.1。

*yieldOnsetMethod*

一个 odb_String，指定用于确定屈服开始的方法。可能的值为"RELATIVE_SLOPE_DROP"和"CLOSURE_VALUE"。默认值为"RELATIVE_SLOPE_DROP"。

*unloadingTable*

一个 odb_SequenceSequenceDouble，指定卸载数据。表数据中的项目如下所述。默认值为空序列。

**表数据**

如果 *variableUnits*=STRESS，加载表数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *variableUnits*=FORCE，加载表数据指定以下内容：
- 力或单位长度的力；此值必须为正。
- 闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *variableUnits*=STRESS 且 *type*=ELASTIC_PLASTIC，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 塑性闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *variableUnits*=FORCE 且 *type*=ELASTIC_PLASTIC，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 塑性闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *variableUnits*=STRESS 且 *type*=DAMAGE，*unloadingTable* 数据指定以下内容：
- 压力；此值必须为正。
- 闭合；此值必须为正。
- 加载垫片时达到的最大闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *variableUnits*=FORCE 且 *type*=DAMAGE，*unloadingTable* 数据指定以下内容：
- 力或单位长度的力；此值必须为正。
- 闭合；此值必须为正。
- 加载垫片时达到的最大闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 GasketThicknessBehavior 对象。

**异常**

RangeError。

### 60.56.2 成员

GasketThicknessBehavior 对象的成员与 [GasketThicknessBehavior](pt02ch60pyo56.md#ker-gasketthicknessbehavior-gasketthicknessbehavior-cpp) 方法的参数具有相同的名称和描述。

此外，GasketThicknessBehavior 对象可以具有以下成员：

**原型**

```
odb_ContactArea contactArea() const;
```

*contactArea*

一个 [ContactArea](pt02ch60pyo25.md) 对象。

### 60.56.3 对应的分析关键字

| [*GASKET THICKNESS BEHAVIOR](../key/key-link.md#usb-kws-mgasketnormal) |
| --- |
