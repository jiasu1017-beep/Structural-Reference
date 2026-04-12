# 60.46 ElectricalConductivity 对象

ElectricalConductivity 对象用于指定电导率。

**访问**

```
materialApi.materials()[*name*].electricalConductivity()
```

### 60.46.1 ElectricalConductivity(...)

此方法创建一个 ElectricalConductivity 对象。

**路径**

```
materialApi.materials()[*name*].ElectricalConductivity
```

**原型**

```
odb_ElectricalConductivity&
ElectricalConductivity(const odb_SequenceSequenceDouble& table,
                       const odb_String& type,
                       bool frequencyDependency,
                       bool temperatureDependency,
                       int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定电导率类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"和"ANISOTROPIC"。默认值为"ISOTROPIC"。

*frequencyDependency*

一个布尔值，指定数据是否依赖频率。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- 电导率。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00221.gif]。
- ![](../graphics/ker_eqn00222.gif]。
- ![](../graphics/ker_eqn00223.gif]。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00221.gif]。
- ![](../graphics/ker_eqn00224.gif]。
- ![](../graphics/ker_eqn00222.gif]。
- ![](../graphics/ker_eqn00225.gif]。
- ![](../graphics/ker_eqn00226.gif]。
- ![](../graphics/ker_eqn00223.gif]。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ElectricalConductivity 对象。

**异常**

RangeError。

### 60.46.2 成员

ElectricalConductivity 对象的成员与 [ElectricalConductivity](pt02ch60pyo46.md#ker-electricalconductivity-electricalconductivity-cpp) 方法的参数具有相同的名称和描述。

### 60.46.3 对应的分析关键字

| [*ELECTRICAL CONDUCTIVITY](../key/key-link.md#usb-kws-melectricconduct) |
| --- |
