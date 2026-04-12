# 60.37 Density 对象

Density 对象用于指定材料密度。

**访问**

```
materialApi.materials()[*name*].density()
```

### 60.37.1 Density(...)

此方法创建一个 Density 对象。

**路径**

```
materialApi.materials()[*name*].Density
```

**原型**

```
odb_Density&
Density(const odb_SequenceSequenceDouble& table,
        bool temperatureDependency,
        int dependencies,
        const odb_String& distributionType,
        const odb_String& fieldName);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*distributionType*

一个 odb_String，指定密度如何空间分布。可能的值为"UNIFORM"、"ANALYTICAL_FIELD"和"DISCRETE_FIELD"。默认值为"UNIFORM"。

*fieldName*

一个 odb_String，指定与该材料选项关联的 [AnalyticalField](#ker-analyticalfield-cpp) 或 [DiscreteField](#ker-discretefield-cpp) 对象的名称。当 *distributionType*="ANALYTICAL_FIELD" 或 *distributionType*="DISCRETE_FIELD" 时，*fieldName* 参数才适用。默认值为空字符串。

**表数据**

- 质量密度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Density 对象。

**异常**

RangeError。

### 60.37.2 成员

Density 对象的成员与 [Density](pt02ch60pyo37.md#ker-density-density-cpp) 方法的参数具有相同的名称和描述。

### 60.37.3 对应的分析关键字

| [*DENSITY](../key/key-link.md#usb-kws-mdensity) |
| --- |
