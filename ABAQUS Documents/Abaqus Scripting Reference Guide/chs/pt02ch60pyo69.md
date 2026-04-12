# 60.69 MohrCoulombHardening 对象

MohrCoulombHardening 对象用于指定 Mohr-Coulomb 塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].mohrCoulombPlasticity()\
.mohrCoulombHardening()
```

### 60.69.1 MohrCoulombHardening(...)

此方法创建一个 MohrCoulombHardening 对象。

**路径**

```
materialApi.materials()[*name*].mohrCoulombPlasticity()\
.MohrCoulombHardening
```

**原型**

```
odb_MohrCoulombHardening&
MohrCoulombHardening(const odb_SequenceSequenceDouble& table,
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

- 内聚屈服应力。
- 对应塑性应变的绝对值。（输入的第一个表值必须始终为零。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 MohrCoulombHardening 对象。

**异常**

RangeError。

### 60.69.2 成员

MohrCoulombHardening 对象的成员与 [MohrCoulombHardening](pt02ch60pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-cpp) 方法的参数具有相同的名称和描述。

### 60.69.3 对应的分析关键字

| [*MOHR COULOMB HARDENING](../key/key-link.md#usb-kws-mmohrcoulombhardening) |
| --- |
