# 60.42 DruckerPrager 对象

DruckerPrager 对象用于指定扩展的 Drucker-Prager 塑性模型。

**访问**

```
materialApi.materials()[*name*].druckerPrager()
```

### 60.42.1 DruckerPrager(...)

此方法创建一个 DruckerPrager 对象。

**路径**

```
materialApi.materials()[*name*].DruckerPrager
```

**原型**

```
odb_DruckerPrager&
DruckerPrager(const odb_SequenceSequenceDouble& table,
              const odb_String& shearCriterion,
              double eccentricity,
              bool testData,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*shearCriterion*

一个 odb_String，指定屈服准则。可能的值为"LINEAR"、"HYPERBOLIC"和"EXPONENTIAL"。默认值为"LINEAR"。

此参数仅适用于 Abaqus/Standard 分析。在 Abaqus/Explicit 分析中仅线性 Drucker-Prager 模型可用。

*eccentricity*

一个 Double，指定流动势偏心率，![](../graphics/ker_eqn00062.gif)，一个定义双曲线流动势接近其渐近线速率的小正数。默认值为 0.1。

此参数仅适用于 Abaqus/Standard 分析。

*testData*

一个布尔值，指定是否由 Abaqus/Standard 根据不同围压水平的三轴试验数据计算指数模型的材料常数。默认值为 false。

此参数仅在 *shearCriterion*="EXPONENTIAL" 时有效。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *shearCriterion*=LINEAR（这是 Abaqus/Explicit 分析中唯一允许的选项），表数据指定以下内容：
- 材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面内。以度为单位给出值。
- ![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力之比。![](../graphics/ker_eqn00110.gif)。如果接受默认值 0.0，则假定值为 1.0。
- 剪胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面内。以度为单位给出值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *shearCriterion*=HYPERBOLIC，表数据指定以下内容：
- 高围压下材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面内。以度为单位给出值。
- 初始静水拉力强度，![](../graphics/ker_eqn00177.gif)。
- 高围压下剪胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面内。以度为单位给出值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *shearCriterion*=EXPONENTIAL，表数据指定以下内容：
- 高围压下剪胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面内。以度为单位给出值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DruckerPrager 对象。

**异常**

RangeError。

### 60.42.2 成员

DruckerPrager 对象的成员与 [DruckerPrager](pt02ch60pyo42.md#ker-druckerprager-druckerprager-cpp) 方法的参数具有相同的名称和描述。

此外，DruckerPrager 对象可以具有以下成员：

**原型**

```
odb_DruckerPragerCreep druckerPragerCreep() const;
odb_DruckerPragerHardening druckerPragerHardening() const;
odb_RateDependent rateDependent() const;
odb_TriaxialTestData triaxialTestData() const;
```

*druckerPragerCreep*

一个 [DruckerPragerCreep](pt02ch60pyo43.md) 对象。

*druckerPragerHardening*

一个 [DruckerPragerHardening](pt02ch60pyo44.md) 对象。

*rateDependent*

一个 [RateDependent](pt02ch60pyo85.md) 对象。

*triaxialTestData*

一个 [TriaxialTestData](pt02ch60pyo99.md) 对象。

### 60.42.3 对应的分析关键字

| [*DRUCKER PRAGER](../key/key-link.md#usb-kws-mdruckerprager) |
| --- |
