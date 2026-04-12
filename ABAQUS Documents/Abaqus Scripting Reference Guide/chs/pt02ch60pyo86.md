# 60.85 RateDependent 对象

RateDependent 对象用于定义率相关粘塑性模型。

**访问**

```
materialApi.materials()[*name*].crushableFoam().rateDependent()
materialApi.materials()[*name*].druckerPrager().rateDependent()
materialApi.materials()[*name*].plastic().rateDependent()
```

### 60.85.1 RateDependent(...)

此方法创建一个 RateDependent 对象。

**路径**

```
materialApi.materials()[*name*].crushableFoam().RateDependent
materialApi.materials()[*name*].druckerPrager().RateDependent
materialApi.materials()[*name*].plastic().RateDependent
```

**原型**

```
odb_RateDependent&
RateDependent(const odb_SequenceSequenceDouble& table,
              const odb_String& type,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定率相关数据的类型。可能的值为"POWER_LAW"、"YIELD_RATIO"和"JOHNSON_COOK"。默认值为"POWER_LAW"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=POWER_LAW，表数据指定以下内容：
- ![](../graphics/ker_eqn00172.gif]。
- ![](../graphics/ker_eqn00088.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=YIELD_RATIO，表数据指定以下内容：
- 屈服应力比，![](../graphics/ker_eqn00357.gif]。
- 等效塑性应变率，![](../graphics/ker_eqn00337.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=JOHNSON_COOK，表数据指定以下内容：
- ![](../graphics/ker_eqn00039.gif]。
- ![](../graphics/ker_eqn00358.gif]。

**返回值**

一个 RateDependent 对象。

**异常**

RangeError。

### 60.85.2 成员

RateDependent 对象的成员与 [RateDependent](pt02ch60pyo85.md#ker-ratedependent-ratedependent-cpp) 方法的参数具有相同的名称和描述。

### 60.85.3 对应的分析关键字

| [*RATE DEPENDENT](../key/key-link.md#usb-kws-mratedependent) |
| --- |
