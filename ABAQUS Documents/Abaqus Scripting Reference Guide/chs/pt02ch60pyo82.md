# 60.82 PorousMetalPlasticity 对象

PorousMetalPlasticity 对象用于指定多孔金属塑性模型。

**访问**

```
materialApi.materials()[*name*].porousMetalPlasticity()
```

### 60.82.1 PorousMetalPlasticity(...)

此方法创建一个 PorousMetalPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].PorousMetalPlasticity
```

**原型**

```
odb_PorousMetalPlasticity&
PorousMetalPlasticity(const odb_SequenceSequenceDouble& table,
                      odb_Union relativeDensity,
                      bool temperatureDependency,
                      int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*relativeDensity*

字符串"NONE"或一个 Double，指定材料的初始相对密度，![](../graphics/ker_eqn00346.gif]。默认值为"NONE"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- ![](../graphics/ker_eqn00347.gif]。
- ![](../graphics/ker_eqn00348.gif]。
- ![](../graphics/ker_eqn00349.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 PorousMetalPlasticity 对象。

**异常**

RangeError。

### 60.82.2 成员

PorousMetalPlasticity 对象的成员与 [PorousMetalPlasticity](pt02ch60pyo82.md#ker-porousmetalplasticity-porousmetalplasticity-cpp) 方法的参数具有相同的名称和描述。

此外，PorousMetalPlasticity 对象可以具有以下成员：

**原型**

```
odb_PorousFailureCriteria porousFailureCriteria() const;
odb_VoidNucleation voidNucleation() const;
```

*porousFailureCriteria*

一个 [PorousFailureCriteria](pt02ch60pyo81.md) 对象。

*voidNucleation*

一个 [VoidNucleation](pt02ch60pyo109.md) 对象。

### 60.82.3 对应的分析关键字

| [*POROUS METAL PLASTICITY](../key/key-link.md#usb-kws-mpormetalplas) |
| --- |
