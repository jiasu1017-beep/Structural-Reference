# 60.77 Plastic 对象

Plastic 对象用于指定金属塑性模型。

**访问**

```
materialApi.materials()[*name*].plastic()
```

### 60.77.1 Plastic(...)

此方法创建一个 Plastic 对象。

**路径**

```
materialApi.materials()[*name*].Plastic
```

**原型**

```
odb_Plastic&
Plastic(const odb_SequenceSequenceDouble& table,
        const odb_String& hardening,
        bool rate,
        const odb_String& dataType,
        bool strainRangeDependency,
        int numBackstresses,
        bool temperatureDependency,
        int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*hardening*

一个 odb_String，指定硬化类型。可能的值为"ISOTROPIC"、"KINEMATIC"、"COMBINED"、"JOHNSON_COOK"和"USER"。默认值为"ISOTROPIC"。

*rate*

一个布尔值，指定数据是否依赖速率。默认值为 false。

*dataType*

一个 odb_String，指定组合硬化的类型。此参数仅在 *hardening*="COMBINED" 时有效。可能的值为"HALF_CYCLE"、"PARAMETERS"和"STABILIZED"。默认值为"HALF_CYCLE"。

*strainRangeDependency*

一个布尔值，指定数据是否依赖应变范围。此参数仅在 *hardening*="COMBINED" 且 *dataType*="STABILIZED" 时有效。默认值为 false。

*numBackstresses*

一个整数，指定背应力数量。此参数仅在 *hardening*="COMBINED" 时有效。默认值为 1。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *hardening*=ISOTROPIC，或者如果 *hardening*=COMBINED 且 *dataType*=HALF_CYCLE，表数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 等效塑性应变率，![](../graphics/ker_eqn00337.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=COMBINED 且 *dataType*=STABILIZED，表数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 应变范围（如果数据依赖应变范围）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=COMBINED 且 *dataType*=PARAMETERS，表数据指定以下内容：
- 零塑性应变时的屈服应力。
- 第一个运动学硬化参数，![](../graphics/ker_eqn00338.gif]。
- 第一个运动学硬化参数，![](../graphics/ker_eqn00339.gif]。
- 如果适用，第二个运动学硬化参数，![](../graphics/ker_eqn00340.gif]。
- 如果适用，第二个运动学硬化参数，![](../graphics/ker_eqn00341.gif]。
- 依此类推。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=KINEMATIC，表数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 温度（如果数据依赖温度）。

如果 *hardening*=JOHNSON_COOK，表数据指定以下内容：
- A。
- B。
- n。
- m。
- 熔化温度。
- 转变温度。

如果 *hardening*=USER，表数据指定以下内容：
- 硬化属性。

**返回值**

一个 Plastic 对象。

**异常**

RangeError。

### 60.77.2 成员

Plastic 对象的成员与 [Plastic](pt02ch60pyo77.md#ker-plastic-plastic-cpp) 方法的参数具有相同的名称和描述。

此外，Plastic 对象可以具有以下成员：

**原型**

```
odb_RateDependent rateDependent() const;
odb_Potential potential() const;
odb_CyclicHardening cyclicHardening() const;
odb_Ornl ornl() const;
odb_CycledPlastic cycledPlastic() const;
odb_AnnealTemperature annealTemperature() const;
```

*rateDependent*

一个 [RateDependent](pt02ch60pyo85.md) 对象。

*potential*

一个 [Potential](pt02ch60pyo83.md) 对象。

*cyclicHardening*

一个 [CyclicHardening](pt02ch60pyo30.md) 对象。

*ornl*

一个 [Ornl](pt02ch60pyo73.md) 对象。

*cycledPlastic*

一个 [CycledPlastic](pt02ch60pyo29.md) 对象。

*annealTemperature*

一个 [AnnealTemperature](pt02ch60pyo03.md) 对象。

### 60.77.3 对应的分析关键字

| [*PLASTIC](../key/key-link.md#usb-kws-mplastic) |
| --- |
