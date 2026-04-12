# 60.89 ShearRetention 对象

ShearRetention 对象用于定义与 [Concrete](pt02ch60pyo18.md) 模型中裂纹表面相关的剪切模量 reduction，作为裂纹间拉伸应变的函数。

**访问**

```
materialApi.materials()[*name*].concrete().shearRetention()
```

### 60.89.1 ShearRetention(...)

此方法创建一个 ShearRetention 对象。

**路径**

```
materialApi.materials()[*name*].concrete().ShearRetention
```

**原型**

```
odb_ShearRetention&
ShearRetention(const odb_SequenceSequenceDouble& table,
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

- 干混凝土的 ![](../graphics/ker_eqn00363.gif)。默认值为 1.0。
- 干混凝土的 ![](../graphics/ker_eqn00364.gif)。默认值为一个非常大的数（完全剪切保持）。
- 湿混凝土的 ![](../graphics/ker_eqn00363.gif)。默认值为 1.0。
- 湿混凝土的 ![](../graphics/ker_eqn00364.gif)。默认值为一个非常大的数（完全剪切保持）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ShearRetention 对象。

**异常**

RangeError。

### 60.89.2 成员

ShearRetention 对象的成员与 [ShearRetention](pt02ch60pyo89.md#ker-shearretention-shearretention-cpp) 方法的参数具有相同的名称和描述。

### 60.89.3 对应的分析关键字

| [*SHEAR RETENTION](../key/key-link.md#usb-kws-mshearretention) |
| --- |
