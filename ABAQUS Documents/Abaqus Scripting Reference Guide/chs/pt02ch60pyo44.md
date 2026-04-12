# 60.44 DruckerPragerHardening 对象

DruckerPragerHardening 对象用于指定 Drucker-Prager 塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].druckerPrager().druckerPragerHardening()
```

### 60.44.1 DruckerPragerHardening(...)

此方法创建一个 DruckerPragerHardening 对象。

**路径**

```
materialApi.materials()[*name*].druckerPrager().DruckerPragerHardening
```

**原型**

```
odb_DruckerPragerHardening&
DruckerPragerHardening(const odb_SequenceSequenceDouble& table,
                       const odb_String& type,
                       bool rate,
                       bool temperatureDependency,
                       int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定定义硬化行为的数据类型。可能的值为"COMPRESSION"、"TENSION"和"SHEAR"。默认值为"COMPRESSION"。

*rate*

一个布尔值，指定数据是否依赖速率。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 屈服应力。
- 对应塑性应变的绝对值。（输入的第一个表值必须始终为零。）
- 此硬化曲线适用的等效塑性应变率，![](../graphics/ker_eqn00181.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DruckerPragerHardening 对象。

**异常**

RangeError。

### 60.44.2 成员

DruckerPragerHardening 对象的成员与 [DruckerPragerHardening](pt02ch60pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-cpp) 方法的参数具有相同的名称和描述。

### 60.44.3 对应的分析关键字

| [*DRUCKER PRAGER HARDENING](../key/key-link.md#usb-kws-mdruckerhardening) |
| --- |
