# 60.93 SoretEffect 对象

SoretEffect 对象用于定义温度梯度驱动的质量扩散。

**访问**

```
materialApi.materials()[*name*].diffusivity().soretEffect()
```

### 60.93.1 SoretEffect(...)

此方法创建一个 SoretEffect 对象。

**路径**

```
materialApi.materials()[*name*].diffusivity().SoretEffect
```

**原型**

```
odb_SoretEffect&
SoretEffect(const odb_SequenceSequenceDouble& table,
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

- Soret 效应因子，![](../graphics/ker_eqn00367.gif]。
- 浓度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 SoretEffect 对象。

**异常**

RangeError。

### 60.93.2 成员

SoretEffect 对象的成员与 [SoretEffect](pt02ch60pyo93.md#ker-soreteffect-soreteffect-cpp) 方法的参数具有相同的名称和描述。

### 60.93.3 对应的分析关键字

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |
