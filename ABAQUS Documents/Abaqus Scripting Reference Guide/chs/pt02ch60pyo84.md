# 60.84 PressureEffect 对象

PressureEffect 对象用于定义等效压力应力驱动的质量扩散。

**访问**

```
materialApi.materials()[*name*].diffusivity().pressureEffect()
```

### 60.84.1 PressureEffect(...)

此方法创建一个 PressureEffect 对象。

**路径**

```
materialApi.materials()[*name*].diffusivity().PressureEffect
```

**原型**

```
odb_PressureEffect&
PressureEffect(const odb_SequenceSequenceDouble& table,
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

- 压力应力因子，![](../graphics/ker_eqn00356.gif]。
- 浓度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 PressureEffect 对象。

**异常**

RangeError。

### 60.84.2 成员

PressureEffect 对象的成员与 [PressureEffect](pt02ch60pyo84.md#ker-pressureeffect-pressureeffect-cpp) 方法的参数具有相同的名称和描述。

### 60.84.3 对应的分析关键字

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |
