# 60.95 SpecificHeat 对象

SpecificHeat 对象用于指定材料的比热容。

**访问**

```
materialApi.materials()[*name*].specificHeat()
```

### 60.95.1 SpecificHeat(...)

此方法创建一个 SpecificHeat 对象。

**路径**

```
materialApi.materials()[*name*].SpecificHeat
```

**原型**

```
odb_SpecificHeat&
SpecificHeat(const odb_SequenceSequenceDouble& table,
             const odb_String& law,
             bool temperatureDependency,
             int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*law*

一个 odb_String，指定比热容行为。可能的值为"CONSTANTVOLUME"和"CONSTANTPRESSURE"。默认值为"CONSTANTVOLUME"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 单位质量比热容。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 SpecificHeat 对象。

**异常**

RangeError。

### 60.95.2 成员

SpecificHeat 对象的成员与 [SpecificHeat](pt02ch60pyo95.md#ker-specificheat-specificheat-cpp) 方法的参数具有相同的名称和描述。

### 60.95.3 对应的分析关键字

| [*SPECIFIC HEAT](../key/key-link.md#usb-kws-mspecificheat) |
| --- |
