# 60.41 Diffusivity 对象

Diffusivity 对象用于指定质量扩散率。

**访问**

```
materialApi.materials()[*name*].diffusivity()
```

### 60.41.1 Diffusivity(...)

此方法创建一个 Diffusivity 对象。

**路径**

```
materialApi.materials()[*name*].Diffusivity
```

**原型**

```
odb_Diffusivity&
Diffusivity(const odb_SequenceSequenceDouble& table,
            const odb_String& type,
            const odb_String& law,
            bool temperatureDependency,
            int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定扩散率类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"和"ANISOTROPIC"。默认值为"ISOTROPIC"。

*law*

一个 odb_String，指定扩散行为。可能的值为"GENERAL"和"FICK"。默认值为"GENERAL"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- 扩散率，![](../graphics/ker_eqn00172.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00174.gif)。
- ![](../graphics/ker_eqn00031.gif)。
- ![](../graphics/ker_eqn00034.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00174.gif)。
- ![](../graphics/ker_eqn00175.gif)。
- ![](../graphics/ker_eqn00031.gif)。
- ![](../graphics/ker_eqn00176.gif)。
- ![](../graphics/ker_eqn00032.gif)。
- ![](../graphics/ker_eqn00034.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Diffusivity 对象。

**异常**

RangeError。

### 60.41.2 成员

Diffusivity 对象的成员与 [Diffusivity](pt02ch60pyo41.md#ker-diffusivity-diffusivity-cpp) 方法的参数具有相同的名称和描述。

此外，Diffusivity 对象可以具有以下成员：

**原型**

```
odb_PressureEffect pressureEffect() const;
odb_SoretEffect soretEffect() const;
```

*pressureEffect*

一个 [PressureEffect](pt02ch60pyo84.md) 对象。

*soretEffect*

一个 [SoretEffect](pt02ch60pyo93.md) 对象。

### 60.41.3 对应的分析关键字

| [*DIFFUSIVITY](../key/key-link.md#usb-kws-mdiffusivity) |
| --- |
