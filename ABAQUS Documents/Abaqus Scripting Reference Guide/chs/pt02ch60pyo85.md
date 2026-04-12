# 60.86 Ratios 对象

Ratios 对象用于指定定义各向异性膨胀的比率。

**访问**

```
materialApi.materials()[*name*].moistureSwelling().ratios()
materialApi.materials()[*name*].swelling().ratios()
```

### 60.86.1 Ratios(...)

此方法创建一个 Ratios 对象。

**路径**

```
materialApi.materials()[*name*].moistureSwelling().Ratios
materialApi.materials()[*name*].swelling().Ratios
```

**原型**

```
odb_Ratios&
Ratios(const odb_SequenceSequenceDouble& table,
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

- ![](../graphics/ker_eqn00359.gif]。
- ![](../graphics/ker_eqn00360.gif]。
- ![](../graphics/ker_eqn00361.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Ratios 对象。

**异常**

RangeError。

### 60.86.2 成员

Ratios 对象的成员与 [Ratios](pt02ch60pyo86.md#ker-ratios-ratios-cpp) 方法的参数具有相同的名称和描述。

### 60.86.3 对应的分析关键字

| [*RATIOS](../key/key-link.md#usb-kws-mswellratios) |
| --- |
