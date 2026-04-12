# 60.43 DruckerPragerCreep 对象

DruckerPragerCreep 对象用于指定 Drucker-Prager 塑性模型的蠕变。

**访问**

```
materialApi.materials()[*name*].druckerPrager().druckerPragerCreep()
```

### 60.43.1 DruckerPragerCreep(...)

此方法创建一个 DruckerPragerCreep 对象。

**路径**

```
materialApi.materials()[*name*].druckerPrager().DruckerPragerCreep
```

**原型**

```
odb_DruckerPragerCreep&
DruckerPragerCreep(const odb_SequenceSequenceDouble& table,
                   const odb_String& law,
                   bool temperatureDependency,
                   int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*law*

一个 odb_String，指定定义蠕变定律的数据类型。可能的值为：
- "STRAIN"，指定应变硬化幂律。
- "TIME"，指定时间硬化幂律。
- "SINGHM"，指定 Singh-Mitchell 型定律。
- "USER"，指定蠕变定律从用户子程序 [`CREEP`](../sub/sub-link.md#sub-xsl-creep) 输入。

默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *law*=TIME 或 *law*=STRAIN，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。（单位为 [F![](../graphics/ker_eqn00178.gif)L![](../graphics/ker_eqn00179.gif)T![](../graphics/ker_eqn00180.gif)](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *law*=SINGHM，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。（单位为 [T1](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00090.gif)。（单位为 [F1L2](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00089.gif)。
- ![](../graphics/ker_eqn00091.gif)。（单位为 [T](../popups/usb-int-iconventions-unitsym.md)。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DruckerPragerCreep 对象。

**异常**

RangeError。

### 60.43.2 成员

DruckerPragerCreep 对象的成员与 [DruckerPragerCreep](pt02ch60pyo43.md#ker-druckerpragercreep-druckerpragercreep-cpp) 方法的参数具有相同的名称和描述。

### 60.43.3 对应的分析关键字

| [*DRUCKER PRAGER CREEP](../key/key-link.md#usb-kws-mdruckerpragercreep) |
| --- |
