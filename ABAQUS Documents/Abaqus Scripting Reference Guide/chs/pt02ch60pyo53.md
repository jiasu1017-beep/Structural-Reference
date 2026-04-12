# 60.53 FluidLeakoff 对象

FluidLeakoff 对象用于指定孔隙压力内聚单元的渗漏系数。

**访问**

```
materialApi.materials()[*name*].fluidLeakoff()
```

### 60.53.1 FluidLeakoff(...)

此方法创建一个 FluidLeakoff 对象。

**路径**

```
materialApi.materials()[*name*].FluidLeakoff
```

**原型**

```
odb_FluidLeakoff&
FluidLeakoff(bool temperatureDependency,
             int dependencies,
             const odb_String& type,
             const odb_SequenceSequenceDouble& table);
```

**必需参数**

无。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*type*

一个 odb_String，指定流体渗漏类型。可能的值为"COEFFICIENTS"和"USER"。默认值为"COEFFICIENTS"。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。默认值为空序列。

**表数据**

表数据指定以下内容：
- 顶部单元表面的流体渗漏系数。
- 底部单元表面的流体渗漏系数。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 FluidLeakoff 对象。

**异常**

无。

### 60.53.2 成员

FluidLeakoff 对象的成员与 [FluidLeakoff](pt02ch60pyo53.md#ker-fluidleakoff-fluidleakoff-cpp) 方法的参数具有相同的名称和描述。

### 60.53.3 对应的分析关键字

| [*FLUID LEAKOFF](../key/key-link.md#usb-kws-mfluidleakoff) |
| --- |
