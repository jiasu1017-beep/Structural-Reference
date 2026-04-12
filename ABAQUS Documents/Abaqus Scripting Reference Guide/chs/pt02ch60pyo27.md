# 60.27 CrushableFoam 对象

CrushableFoam 对象用于指定可压碎泡沫塑性模型。

**访问**

```
materialApi.materials()[*name*].crushableFoam()
```

### 60.27.1 CrushableFoam(...)

此方法创建一个 CrushableFoam 对象。

**路径**

```
materialApi.materials()[*name*].CrushableFoam
```

**原型**

```
odb_CrushableFoam&
CrushableFoam(const odb_SequenceSequenceDouble& table,
              const odb_String& hardening,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*hardening*

一个 odb_String，指定硬化/软化定义的类型。可能的值为"VOLUMETRIC"和"ISOTROPIC"。默认值为"VOLUMETRIC"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *hardening*=VOLUMETRIC，表数据指定以下内容：
- 单轴压缩初始屈服应力 ![](../graphics/ker_eqn00152.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值，![](../graphics/ker_eqn00143.gif)；0.0 ![](../graphics/ker_eqn00154.gif) 3.0。
- 静水拉伸屈服应力 ![](../graphics/ker_eqn00156.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值，![](../graphics/ker_eqn00155.gif)。默认值为 1.0。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=ISOTROPIC，表数据指定以下内容：
- 单轴压缩初始屈服应力 ![](../graphics/ker_eqn00152.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值，![](../graphics/ker_eqn00143.gif)；0.0 ![](../graphics/ker_eqn00157.gif) 3.0。
- 塑性泊松比。![](../graphics/ker_eqn00158.gif)；-1 ![](../graphics/ker_eqn00159.gif) 0.5。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CrushableFoam 对象。

**异常**

RangeError。

### 60.27.2 成员

CrushableFoam 对象的成员与 [CrushableFoam](pt02ch60pyo27.md#ker-crushablefoam-crushablefoam-cpp) 方法的参数具有相同的名称和描述。

此外，CrushableFoam 对象可以具有以下成员：

**原型**

```
odb_CrushableFoamHardening crushableFoamHardening() const;
odb_RateDependent rateDependent() const;
```

*crushableFoamHardening*

一个 [CrushableFoamHardening](pt02ch60pyo28.md) 对象。

*rateDependent*

一个 [RateDependent](pt02ch60pyo85.md) 对象。

### 60.27.3 对应的分析关键字

| [*CRUSHABLE FOAM](../key/key-link.md#usb-kws-mcrushfoam) |
| --- |
