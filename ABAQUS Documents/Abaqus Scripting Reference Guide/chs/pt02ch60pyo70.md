# 60.70 MohrCoulombPlasticity 对象

MohrCoulombPlasticity 对象用于指定扩展的 Mohr-Coulomb 塑性模型。

**访问**

```
materialApi.materials()[*name*].mohrCoulombPlasticity()
```

### 60.70.1 MohrCoulombPlasticity(...)

此方法创建一个 MohrCoulombPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].MohrCoulombPlasticity
```

**原型**

```
odb_MohrCoulombPlasticity&
MohrCoulombPlasticity(const odb_SequenceSequenceDouble& table,
                      odb_Union deviatoricEccentricity,
                      double meridionalEccentricity,
                      bool temperatureDependency,
                      int dependencies,
                      bool useTensionCutoff);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*deviatoricEccentricity*

字符串"NONE"或一个 Double，指定偏平面中的流动势偏心率，![](../graphics/ker_eqn00289.gif)；1/2 ![](../graphics/ker_eqn00290.gif) 1.0。如果 *deviatoricEccentricity*="NONE"，Abaqus 使用指定的 Mohr-Coulomb 摩擦角计算值。默认值为"NONE"。

*meridionalEccentricity*

一个 Double，指定子午平面中的流动势偏心率，![](../graphics/ker_eqn00062.gif]。默认值为 0.1。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*useTensionCutoff*

一个布尔值，指定是否需要拉伸截断规范。默认值为 false。

**表数据**

表数据指定以下内容：
- 高围压下 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00292.gif) 平面内的摩擦角（以度为单位），![](../graphics/ker_eqn00291.gif]。
- 高围压下 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00293.gif) 平面内的剪胀角，![](../graphics/ker_eqn00132.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 MohrCoulombPlasticity 对象。

**异常**

RangeError。

### 60.70.2 成员

MohrCoulombPlasticity 对象的成员与 [MohrCoulombPlasticity](pt02ch60pyo70.md#ker-mohrcoulombplasticity-mohrcoulombplasticity-cpp) 方法的参数具有相同的名称和描述。

此外，MohrCoulombPlasticity 对象可以具有以下成员：

**原型**

```
odb_MohrCoulombHardening mohrCoulombHardening() const;
odb_TensionCutOff tensionCutOff() const;
```

*mohrCoulombHardening*

一个 [MohrCoulombHardening](pt02ch60pyo69.md) 对象。

*tensionCutOff*

一个 [TensionCutOff](pt02ch60pyo97.md) 对象。

### 60.70.3 对应的分析关键字

| [*MOHR COULOMB](../key/key-link.md#usb-kws-mmohrcoulomb) |
| --- |
