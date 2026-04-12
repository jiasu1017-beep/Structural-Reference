# 60.16 ClayPlasticity 对象

ClayPlasticity 对象用于指定扩展 Cam-粘土塑性模型。

**访问**

```
materialApi.materials()[*name*].clayPlasticity()
```

### 60.16.1 ClayPlasticity(...)

此方法创建一个 ClayPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].ClayPlasticity
```

**原型**

```
odb_ClayPlasticity&
ClayPlasticity(const odb_SequenceSequenceDouble& table,
               odb_Union intercept,
               const odb_String& hardening,
               bool temperatureDependency,
               int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*intercept*

字符串"NONE"或一个 Double，指定 ![](../graphics/ker_eqn00106.gif)，即在孔隙比与压力应力对数的图中，原始压缩线与孔隙比轴的截距。默认值为"NONE"。

此参数仅在 *hardening*="EXPONENTIAL" 时有效。

*hardening*

一个 odb_String，指定硬化/软化定义的类型。可能的值为"EXPONENTIAL"和"TABULAR"。默认值为"EXPONENTIAL"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *hardening*=EXPONENTIAL，表数据指定以下内容：
- 对数塑性体积模量，![](../graphics/ker_eqn00107.gif)（无量纲）。
- 临界状态应力比，![](../graphics/ker_eqn00108.gif)。
- 初始屈服面大小，![](../graphics/ker_eqn00109.gif)。
- ![](../graphics/ker_eqn00095.gif)，定义临界状态"湿"侧屈服面大小的参数。
- ![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力之比。![](../graphics/ker_eqn00110.gif)。如果接受默认值 0.0，则假定值为 1.0。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=TABULAR，表数据指定以下内容：
- 临界状态应力比，![](../graphics/ker_eqn00108.gif)。
- 对应于 ![](../graphics/ker_eqn00112.gif) 的初始体积塑性应变，![](../graphics/ker_eqn00111.gif)，根据 [ClayHardening](pt02ch60pyo15.md) 定义。
- ![](../graphics/ker_eqn00095.gif)，定义临界状态"湿"侧屈服面大小的参数。
- ![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力之比。![](../graphics/ker_eqn00110.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ClayPlasticity 对象。

**异常**

RangeError。

### 60.16.2 成员

ClayPlasticity 对象的成员与 [ClayPlasticity](pt02ch60pyo16.md#ker-clayplasticity-clayplasticity-cpp) 方法的参数具有相同的名称和描述。

此外，ClayPlasticity 对象可以具有以下成员：

**原型**

```
odb_ClayHardening clayHardening() const;
```

*clayHardening*

一个 [ClayHardening](pt02ch60pyo15.md) 对象。

### 60.16.3 对应的分析关键字

| [*CLAY PLASTICITY](../key/key-link.md#usb-kws-mclayplast) |
| --- |
