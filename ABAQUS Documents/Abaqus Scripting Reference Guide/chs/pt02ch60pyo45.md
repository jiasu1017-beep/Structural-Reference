# 60.45 Elastic 对象

Elastic 对象用于指定弹性材料特性。

**访问**

```
materialApi.materials()[*name*].elastic()
```

### 60.45.1 Elastic(...)

此方法创建一个 Elastic 对象。

**路径**

```
materialApi.materials()[*name*].Elastic
```

**原型**

```
odb_Elastic&
Elastic(const odb_SequenceSequenceDouble& table,
        const odb_String& type,
        bool noCompression,
        bool noTension,
        bool temperatureDependency,
        int dependencies,
        const odb_String& moduli);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定提供的弹性数据类型。可能的值为：
- "ISOTROPIC"
- "ORTHOTROPIC"
- "ANISOTROPIC"
- "ENGINEERING_CONSTANTS"
- "LAMINA"
- "TRACTION"
- "COUPLED_TRACTION"
- "SHORT_FIBER"
- "SHEAR"

默认值为"ISOTROPIC"。

*noCompression*

一个布尔值，指定是否允许压应力。默认值为 false。

*noTension*

一个布尔值，指定是否允许拉应力。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*moduli*

一个 odb_String，指定弹性材料常数的时间依赖性。可能的值为"INSTANTANEOUS"和"LONG_TERM"。默认值为"LONG_TERM"。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- 杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=SHEAR，表数据指定以下内容：
- 剪切模量，![](../graphics/ker_eqn00182.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENGINEERING_CONSTANTS，表数据指定以下内容：
- ![](../graphics/ker_eqn00183.gif)。
- ![](../graphics/ker_eqn00184.gif)。
- ![](../graphics/ker_eqn00185.gif)。
- ![](../graphics/ker_eqn00186.gif)。
- ![](../graphics/ker_eqn00187.gif)。
- ![](../graphics/ker_eqn00188.gif)。
- ![](../graphics/ker_eqn00189.gif)。
- ![](../graphics/ker_eqn00190.gif)。
- ![](../graphics/ker_eqn00191.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=LAMINA，表数据指定以下内容：
- ![](../graphics/ker_eqn00183.gif)。
- ![](../graphics/ker_eqn00184.gif)。
- ![](../graphics/ker_eqn00186.gif)。
- ![](../graphics/ker_eqn00189.gif)。
- ![](../graphics/ker_eqn00190.gif)。此剪切模量用于定义壳中的横向剪切行为。
- ![](../graphics/ker_eqn00191.gif)。此剪切模量用于定义壳中的横向剪切行为。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00192.gif)。
- ![](../graphics/ker_eqn00193.gif)。
- ![](../graphics/ker_eqn00194.gif)。
- ![](../graphics/ker_eqn00195.gif)。
- ![](../graphics/ker_eqn00196.gif)。
- ![](../graphics/ker_eqn00197.gif)。
- ![](../graphics/ker_eqn00198.gif)。
- ![](../graphics/ker_eqn00199.gif)。
- ![](../graphics/ker_eqn00200.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00192.gif)。
- ![](../graphics/ker_eqn00193.gif)。
- ![](../graphics/ker_eqn00194.gif)。
- ![](../graphics/ker_eqn00195.gif)。
- ![](../graphics/ker_eqn00196.gif)。
- ![](../graphics/ker_eqn00197.gif)。
- ![](../graphics/ker_eqn00201.gif)。
- ![](../graphics/ker_eqn00202.gif)。
- ![](../graphics/ker_eqn00203.gif)。
- ![](../graphics/ker_eqn00198.gif)。
- ![](../graphics/ker_eqn00204.gif)。
- ![](../graphics/ker_eqn00205.gif)。
- ![](../graphics/ker_eqn00206.gif)。
- ![](../graphics/ker_eqn00207.gif)。
- ![](../graphics/ker_eqn00199.gif)。
- ![](../graphics/ker_eqn00208.gif)。
- ![](../graphics/ker_eqn00209.gif)。
- ![](../graphics/ker_eqn00210.gif)。
- ![](../graphics/ker_eqn00211.gif)。
- ![](../graphics/ker_eqn00212.gif)。
- ![](../graphics/ker_eqn00200.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=TRACTION，表数据指定以下内容：
- 对于翘曲单元为 ![](../graphics/ker_eqn00163.gif]；对于内聚单元为 ![](../graphics/ker_eqn00213.gif)。
- 对于翘曲单元为 ![](../graphics/ker_eqn00214.gif]；对于内聚单元为 ![](../graphics/ker_eqn00215.gif]。
- 对于翘曲单元为 ![](../graphics/ker_eqn00216.gif]；对于内聚单元为 ![](../graphics/ker_eqn00217.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=COUPLED_TRACTION，表数据指定以下内容：
- ![](../graphics/ker_eqn00213.gif]。
- ![](../graphics/ker_eqn00215.gif]。
- ![](../graphics/ker_eqn00217.gif]。
- ![](../graphics/ker_eqn00218.gif]。
- ![](../graphics/ker_eqn00219.gif]。
- ![](../graphics/ker_eqn00220.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=SHORT_FIBER，则没有表数据。

**返回值**

一个 Elastic 对象。

**异常**

RangeError。

### 60.45.2 成员

Elastic 对象的成员与 [Elastic](pt02ch60pyo45.md#ker-elastic-elastic-cpp) 方法的参数具有相同的名称和描述。

此外，Elastic 对象可以具有以下成员：

**原型**

```
odb_FailStress failStress() const;
odb_FailStrain failStrain() const;
```

*failStress*

一个 [FailStress](pt02ch60pyo51.md) 对象。

*failStrain*

一个 [FailStrain](pt02ch60pyo50.md) 对象。

### 60.45.3 对应的分析关键字

| [*ELASTIC](../key/key-link.md#usb-kws-melastic) |
| --- |
