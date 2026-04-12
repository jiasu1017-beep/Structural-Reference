# 60.24 Conductivity 对象

Conductivity 对象用于指定热导率。

**访问**

```
materialApi.materials()[*name*].conductivity()
```

### 60.24.1 Conductivity(...)

此方法创建一个 Conductivity 对象。

**路径**

```
materialApi.materials()[*name*].Conductivity
```

**原型**

```
odb_Conductivity&
Conductivity(const odb_SequenceSequenceDouble& table,
             const odb_String& type,
             bool temperatureDependency,
             int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定电导率类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"和"ANISOTROPIC"。默认值为"ISOTROPIC"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- 电导率，![](../graphics/ker_eqn00143.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif)。
- ![](../graphics/ker_eqn00145.gif)。
- ![](../graphics/ker_eqn00146.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif)。
- ![](../graphics/ker_eqn00147.gif)。
- ![](../graphics/ker_eqn00145.gif)。
- ![](../graphics/ker_eqn00148.gif)。
- ![](../graphics/ker_eqn00149.gif)。
- ![](../graphics/ker_eqn00146.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Conductivity 对象。

**异常**

RangeError。

### 60.24.2 成员

Conductivity 对象的成员与 [Conductivity](pt02ch60pyo24.md#ker-conductivity-conductivity-cpp) 方法的参数具有相同的名称和描述。

### 60.24.3 对应的分析关键字

| [*CONDUCTIVITY](../key/key-link.md#usb-kws-mconductivity) |
| --- |
