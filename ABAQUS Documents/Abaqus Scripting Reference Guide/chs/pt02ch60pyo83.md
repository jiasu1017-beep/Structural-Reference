# 60.83 Potential 对象

Potential 对象用于定义各向异性屈服/蠕变模型。

**访问**

```
materialApi.materials()[*name*].creep().potential()
materialApi.materials()[*name*].plastic().potential()
materialApi.materials()[*name*].viscous().potential()
```

### 60.83.1 Potential(...)

此方法创建一个 Potential 对象。

**路径**

```
materialApi.materials()[*name*].creep().Potential
materialApi.materials()[*name*].plastic().Potential
materialApi.materials()[*name*].viscous().Potential
```

**原型**

```
odb_Potential&
Potential(const odb_SequenceSequenceDouble& table,
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

- ![](../graphics/ker_eqn00350.gif]。
- ![](../graphics/ker_eqn00351.gif]。
- ![](../graphics/ker_eqn00352.gif]。
- ![](../graphics/ker_eqn00353.gif]。
- ![](../graphics/ker_eqn00354.gif]。
- ![](../graphics/ker_eqn00355.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Potential 对象。

**异常**

RangeError。

### 60.83.2 成员

Potential 对象的成员与 [Potential](pt02ch60pyo83.md#ker-potential-potential-cpp) 方法的参数具有相同的名称和描述。

### 60.83.3 对应的分析关键字

| [*POTENTIAL](../key/key-link.md#usb-kws-mpotential) |
| --- |
