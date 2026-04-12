# 60.36 DeformationPlasticity 对象

DeformationPlasticity 对象用于指定变形塑性模型。

**访问**

```
materialApi.materials()[*name*].deformationPlasticity()
```

### 60.36.1 DeformationPlasticity(...)

此方法创建一个 DeformationPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].DeformationPlasticity
```

**原型**

```
odb_DeformationPlasticity&
DeformationPlasticity(const odb_SequenceSequenceDouble& table,
                      bool temperatureDependency);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

**表数据**

- 杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 屈服应力，![](../graphics/ker_eqn00165.gif)。
- 指数，![](../graphics/ker_eqn00088.gif)。
- 屈服偏移，![](../graphics/ker_eqn00090.gif)。
- 温度（如果数据依赖温度）。

**返回值**

一个 DeformationPlasticity 对象。

**异常**

RangeError。

### 60.36.2 成员

DeformationPlasticity 对象的成员与 [DeformationPlasticity](pt02ch60pyo36.md#ker-deformationplasticity-deformationplasticity-cpp) 方法的参数具有相同的名称和描述。

### 60.36.3 对应的分析关键字

| [*DEFORMATION PLASTICITY](../key/key-link.md#usb-kws-mdeformplas) |
| --- |
