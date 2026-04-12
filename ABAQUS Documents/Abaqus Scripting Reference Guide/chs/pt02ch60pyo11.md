# 60.11 CapPlasticity 对象

CapPlasticity 对象用于指定修正的 Drucker-Prager/帽盖塑性模型。

**访问**

```
materialApi.materials()[*name*].capPlasticity()
```

### 60.11.1 CapPlasticity(...)

此方法创建一个 CapPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].CapPlasticity
```

**原型**

```
odb_CapPlasticity&
CapPlasticity(const odb_SequenceSequenceDouble& table,
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

- 材料内聚力，![](../graphics/ker_eqn00082.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面（Abaqus/Standard）或 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面（Abaqus/Explicit）。
- 材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面（Abaqus/Standard）或 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面（Abaqus/Explicit）。以度为单位给出值。
- 帽盖偏心率参数，![](../graphics/ker_eqn00096.gif)。其值必须大于零（通常为 0.0 ![](../graphics/ker_eqn00097.gif) 1.0）。
- 初始帽盖屈服面位置，![](../graphics/ker_eqn00098.gif)。
- 过渡面半径参数，![](../graphics/ker_eqn00090.gif)。默认值为 0.0（即无过渡面）。
-（在 Abaqus/Explicit 中不使用）![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力之比。可能的值为 0.778 ![](../graphics/ker_eqn00100.gif) 1.0。如果接受默认值 0.0，Abaqus/Standard 假定 ![](../graphics/ker_eqn00101.gif) 1.0。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapPlasticity 对象。

**异常**

RangeError。

### 60.11.2 成员

CapPlasticity 对象的成员与 [CapPlasticity](pt02ch60pyo11.md#ker-capplasticity-capplasticity-cpp) 方法的参数具有相同的名称和描述。

此外，CapPlasticity 对象可以具有以下成员：

**原型**

```
odb_CapCreepCohesion capCreepCohesion() const;
odb_CapCreepConsolidation capCreepConsolidation() const;
odb_CapHardening capHardening() const;
```

*capCreepCohesion*

一个 [CapCreepCohesion](pt02ch60pyo08.md) 对象。

*capCreepConsolidation*

一个 [CapCreepConsolidation](pt02ch60pyo09.md) 对象。

*capHardening*

一个 [CapHardening](pt02ch60pyo10.md) 对象。

### 60.11.3 对应的分析关键字

| [*CAP PLASTICITY](../key/key-link.md#usb-kws-mcapplasticity) |
| --- |
