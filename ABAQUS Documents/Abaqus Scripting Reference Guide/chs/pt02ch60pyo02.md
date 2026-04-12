# 60.2 AcousticMedium 对象

AcousticMedium 对象用于指定材料的声学特性。

**访问**

```
materialApi.materials()[*name*].acousticMedium()
```

### 60.2.1 AcousticMedium(...)

此方法创建一个 AcousticMedium 对象。

**路径**

```
materialApi.materials()[*name*].AcousticMedium
```

**原型**

```
odb_AcousticMedium&
AcousticMedium(bool acousticVolumetricDrag,
           bool temperatureDependencyB,
           bool temperatureDependencyV,
           int dependenciesB,
           int dependenciesV,
           const odb_SequenceSequenceDouble& bulkTable,
           const odb_SequenceSequenceDouble& volumetricTable);
```

**必需参数**

无。

**可选参数**

*acousticVolumetricDrag*

一个布尔值，指定是否指定了 volumetricTable 数据。默认值为 false。

*temperatureDependencyB*

一个布尔值，指定 *bulkTable* 中的数据是否依赖温度。默认值为 false。

*temperatureDependencyV*

一个布尔值，指定 *volumetricTable* 中的数据是否依赖温度。默认值为 false。

*dependenciesB*

一个整数，指定 *bulkTable* 中数据的场变量依赖数量。默认值为 0。

*dependenciesV*

一个整数，指定 *volumetricTable* 中数据的场变量依赖数量。默认值为 0。

*bulkTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- 体积模量。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

默认值为空序列。

*volumetricTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- 体积阻力。
- 频率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

默认值为空序列。

**返回值**

一个 AcousticMedium 对象。

**异常**

RangeError。

### 60.2.2 成员

AcousticMedium 对象的成员与 [AcousticMedium](pt02ch60pyo02.md#ker-acousticmedium-acousticmedium-cpp) 方法的参数具有相同的名称和描述。

### 60.2.3 对应的分析关键字

| [*ACOUSTIC MEDIUM](../key/key-link.md#usb-kws-macousticmed) |
| --- |
