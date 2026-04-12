# 60.3 AnnealTemperature 对象

AnnealTemperature 对象用于指定材料退火温度。

**访问**

```
materialApi.materials()[*name*].plastic().annealTemperature()
```

### 60.3.1 AnnealTemperature(...)

此方法创建一个 AnnealTemperature 对象。

**路径**

```
materialApi.materials()[*name*].plastic().AnnealTemperature
```

**原型**

```
odb_AnnealTemperature&
AnnealTemperature(const odb_SequenceSequenceDouble& table,
                  int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 退火温度，![](../graphics/ker_eqn00053.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 AnnealTemperature 对象。

**异常**

RangeError。

### 60.3.2 成员

AnnealTemperature 对象的成员与 [AnnealTemperature](pt02ch60pyo03.md#ker-annealtemperature-annealtemperature-cpp) 方法的参数具有相同的名称和描述。

### 60.3.3 对应的分析关键字

| [*ANNEAL TEMPERATURE](../key/key-link.md#usb-kws-mannealtemp) |
| --- |
