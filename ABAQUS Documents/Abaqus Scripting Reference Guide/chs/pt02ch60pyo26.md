# 60.26 Creep 对象

Creep 对象定义蠕变定律。

**访问**

```
materialApi.materials()[*name*].creep()
```

### 60.26.1 Creep(...)

此方法创建一个 Creep 对象。

**路径**

```
materialApi.materials()[*name*].Creep
```

**原型**

```
odb_Creep&
Creep(const odb_SequenceSequenceDouble& table,
      const odb_String& law,
      bool temperatureDependency,
      int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*law*

一个 odb_String，指定应变硬化定律。可能的值为"STRAIN"、"TIME"、"HYPERBOLIC_SINE"和"USER"。默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *law*=STRAIN 或 *law*=TIME，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *law*=HYPERBOLIC_SINE，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00150.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00151.gif)（如果数据依赖温度）。
- ![](../graphics/ker_eqn00096.gif)。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Creep 对象。

**异常**

RangeError。

### 60.26.2 成员

Creep 对象的成员与 [Creep](pt02ch60pyo26.md#ker-creep-creep-cpp) 方法的参数具有相同的名称和描述。

此外，Creep 对象可以具有以下成员：

**原型**

```
odb_Ornl ornl() const;
odb_Potential potential() const;
```

*ornl*

一个 [Ornl](pt02ch60pyo73.md) 对象。

*potential*

一个 [Potential](pt02ch60pyo83.md) 对象。

### 60.26.3 对应的分析关键字

| [*CREEP](../key/key-link.md#usb-kws-mcreep) |
| --- |
