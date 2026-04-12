# 60.68 MagneticPermeability 对象

MagneticPermeability 对象用于指定磁导率。

**访问**

```
materialApi.materials()[*name*].magneticPermeability()
```

### 60.68.1 MagneticPermeability(...)

此方法创建一个 MagneticPermeability 对象。

**路径**

```
materialApi.materials()[*name*].MagneticPermeability
```

**原型**

```
odb_MagneticPermeability&
MagneticPermeability(const odb_SequenceSequenceDouble& table,
                    const odb_SequenceSequenceDouble& table2,
                    const odb_SequenceSequenceDouble& table3,
                    const odb_String& type,
                    bool frequencyDependency,
                    bool temperatureDependency,
                    int dependencies,
                    bool nonlinearBH);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

*table2*

一个 odb_SequenceSequenceDouble，如果 Nonlinear BH 选项为真，则必须指定 table2。table2 的项目与 table 类似，但适用于第二方向。

*table3*

一个 odb_SequenceSequenceDouble，如果 Nonlinear BH 选项为真，则必须指定 table3。table3 的项目与 table 类似，但适用于第三方向。

**可选参数**

*type*

一个 odb_String，指定磁导率类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"和"ANISOTROPIC"。默认值为"ISOTROPIC"。

*frequencyDependency*

一个布尔值，指定数据是否依赖频率。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*nonlinearBH*

一个布尔值，指定磁行为是否非线性的，并以磁通密度与磁场值的表格形式提供。默认值为 false。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- 磁导率。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ISOTROPIC 且 *nonlinearBH*=TRUE，表数据指定以下内容：
- 磁通密度矢量的大小。
- 磁场矢量的大小。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00428.gif]。
- ![](../graphics/ker_eqn00429.gif]。
- ![](../graphics/ker_eqn00430.gif]。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC 且 *nonlinearBH*=TRUE，表数据指定以下内容：
- 第一方向磁通密度矢量的大小。
- 第二方向磁场矢量的大小。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00431.gif]。
- ![](../graphics/ker_eqn00432.gif]。
- ![](../graphics/ker_eqn00429.gif]。
- ![](../graphics/ker_eqn00433.gif]。
- ![](../graphics/ker_eqn00434.gif]。
- ![](../graphics/ker_eqn00430.gif]。
- 频率（如果数据依赖频率）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC 且 *nonlinearBH*=TRUE，表数据指定以下内容：
- 第一方向磁通密度矢量的大小。
- 第三方向磁场矢量的大小。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 MagneticPermeability 对象。

**异常**

RangeError。

### 60.68.2 成员

MagneticPermeability 对象的成员与 [MagneticPermeability](pt02ch60pyo68.md#ker-magneticpermeability-magneticpermeability-cpp) 方法的参数具有相同的名称和描述。

### 60.68.3 对应的分析关键字

| [*MAGNETIC PERMEABILITY](../key/key-link.md#usb-kws-mmagpermeability) |
| --- |
