# 60.15 ClayHardening 对象

ClayHardening 对象用于指定粘土塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].clayPlasticity().clayHardening()
```

### 60.15.1 ClayHardening(...)

此方法创建一个 ClayHardening 对象。

**路径**

```
materialApi.materials()[*name*].clayPlasticity().ClayHardening
```

**原型**

```
odb_ClayHardening&
ClayHardening(const odb_SequenceSequenceDouble& table,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 屈服时的静水压力应力，![](../graphics/ker_eqn00105.gif)。
- 对应体积塑性应变的绝对值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ClayHardening 对象。

**异常**

RangeError。

### 60.15.2 成员

ClayHardening 对象的成员与 [ClayHardening](pt02ch60pyo15.md#ker-clayhardening-clayhardening-cpp) 方法的参数具有相同的名称和描述。

### 60.15.3 对应的分析关键字

| [*CLAY HARDENING](../key/key-link.md#usb-kws-mclayhardening) |
| --- |
