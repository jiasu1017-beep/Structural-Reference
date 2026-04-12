# 60.78 PoreFluidExpansion 对象

PoreFluidExpansion 对象用于指定液压流体的热膨胀系数。

**访问**

```
materialApi.materials()[*name*].poreFluidExpansion()
```

### 60.78.1 PoreFluidExpansion(...)

此方法创建一个 PoreFluidExpansion 对象。

**路径**

```
materialApi.materials()[*name*].PoreFluidExpansion
```

**原型**

```
odb_PoreFluidExpansion&
PoreFluidExpansion(const odb_SequenceSequenceDouble& table,
                   double zero,
                   bool temperatureDependency,
                   int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*zero*

一个 Double，指定 ![](../graphics/ker_eqn00061.gif] 的值。默认值为 0.0。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 平均热膨胀系数，![](../graphics/ker_eqn00239.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 PoreFluidExpansion 对象。

**异常**

RangeError。

### 60.78.2 成员

PoreFluidExpansion 对象的成员与 [PoreFluidExpansion](pt02ch60pyo78.md#ker-porefluidexpansion-porefluidexpansion-cpp) 方法的参数具有相同的名称和描述。

### 60.78.3 对应的分析关键字

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |
