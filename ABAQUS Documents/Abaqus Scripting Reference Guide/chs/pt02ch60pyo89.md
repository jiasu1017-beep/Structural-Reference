# 60.88 SaturationDependence 对象

SaturationDependence 对象用于指定材料渗透率对润湿液体饱和度的依赖关系。

**访问**

```
materialApi.materials()[*name*].permeability().saturationDependence()
```

### 60.88.1 SaturationDependence(...)

此方法创建一个 SaturationDependence 对象。

**路径**

```
materialApi.materials()[*name*].permeability().SaturationDependence
```

**原型**

```
odb_SaturationDependence&
SaturationDependence(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- ![](../graphics/ker_eqn00362.gif]。（无量纲。）
- 饱和度，![](../graphics/ker_eqn00234.gif]。（无量纲。）

**返回值**

一个 SaturationDependence 对象。

**异常**

RangeError。

### 60.88.2 成员

SaturationDependence 对象的成员与 [SaturationDependence](pt02ch60pyo88.md#ker-saturationdependence-saturationdependence-cpp) 方法的参数具有相同的名称和描述。

### 60.88.3 对应的分析关键字

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |
