# 60.74 Permeability 对象

Permeability 对象用于定义孔隙流体渗透率。

**访问**

```
materialApi.materials()[*name*].permeability()
```

### 60.74.1 Permeability(...)

此方法创建一个 Permeability 对象。

**路径**

```
materialApi.materials()[*name*].Permeability
```

**原型**

```
odb_Permeability&
Permeability(double specificWeight,
             double inertialDragCoefficient,
             const odb_SequenceSequenceDouble& table,
             const odb_String& type,
             bool temperatureDependency,
             int dependencies);
```

**必需参数**

*specificWeight*

一个 Double，指定润湿液体的比重，![](../graphics/ker_eqn00296.gif]。

*inertialDragCoefficient*

一个 Double，指定润湿液体的惯性拖曳系数，![](../graphics/ker_eqn00296.gif]。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定渗透率类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"、"ANISOTROPIC"、"ISOTROPIC-CFD"和"CARMAN_KOZENY"。默认值为"ISOTROPIC"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00143.gif]。
- 孔隙比，![](../graphics/ker_eqn00289.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif]。
- ![](../graphics/ker_eqn00145.gif]。
- ![](../graphics/ker_eqn00146.gif]。
- 孔隙比，![](../graphics/ker_eqn00289.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif]。
- ![](../graphics/ker_eqn00147.gif]。
- ![](../graphics/ker_eqn00145.gif]。
- ![](../graphics/ker_eqn00148.gif]。
- ![](../graphics/ker_eqn00149.gif]。
- ![](../graphics/ker_eqn00146.gif]。
- 孔隙比，![](../graphics/ker_eqn00289.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=ISOTROPIC_CFD，表数据指定以下内容：
- ![](../graphics/ker_eqn00143.gif]。
- 孔隙率，![](../graphics/ker_eqn00289.gif]。

如果 *type*=CARMAN_KOZENY，表数据指定以下内容：
- Kozeny 常量![](../graphics/ker_eqn00289.gif]。
- 孔隙粒子半径，![](../graphics/ker_eqn00289.gif]。

**返回值**

一个 Permeability 对象。

**异常**

RangeError。

### 60.74.2 成员

Permeability 对象的成员与 [Permeability](pt02ch60pyo74.md#ker-permeability-permeability-cpp) 方法的参数具有相同的名称和描述。

此外，Permeability 对象可以具有以下成员：

**原型**

```
odb_SaturationDependence saturationDependence() const;
odb_VelocityDependence velocityDependence() const;
```

*saturationDependence*

一个 [SaturationDependence](pt02ch60pyo88.md) 对象，指定材料渗透率对润湿液体饱和度的依赖关系。

*velocityDependence*

一个 [VelocityDependence](pt02ch60pyo105.md) 对象，指定材料渗透率对流体流速的依赖关系。

### 60.74.3 对应的分析关键字

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |
