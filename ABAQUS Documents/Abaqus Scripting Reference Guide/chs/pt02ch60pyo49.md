# 60.49 Expansion 对象

Expansion 对象用于指定热膨胀。

**访问**

```
materialApi.materials()[*name*].expansion()
```

### 60.49.1 Expansion(...)

此方法创建一个 Expansion 对象。

**路径**

```
materialApi.materials()[*name*].Expansion
```

**原型**

```
odb_Expansion&
Expansion(const odb_String& type,
          bool userSubroutine,
          double zero,
          bool temperatureDependency,
          int dependencies,
          const odb_SequenceSequenceDouble& table);
```

**必需参数**

无。

**可选参数**

*type*

一个 odb_String，指定膨胀类型。可能的值为"ISOTROPIC"、"ORTHOTROPIC"、"ANISOTROPIC"和"SHORT_FIBER"。默认值为"ISOTROPIC"。

*userSubroutine*

一个布尔值，指定是否使用用户子程序来定义热应变的增量。默认值为 false。

*zero*

一个 Double，如果热膨胀依赖于温度或场变量，指定 ![](../graphics/ker_eqn00061.gif) 的值。默认值为 0.0。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。默认值为空序列。

此参数仅在 *type* 不是"USER"时需要。

**表数据**

如果 *type*=ISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00239.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00240.gif]。
- ![](../graphics/ker_eqn00241.gif]。
- ![](../graphics/ker_eqn00242.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表数据指定以下内容：
- ![](../graphics/ker_eqn00240.gif]。
- ![](../graphics/ker_eqn00241.gif]。
- ![](../graphics/ker_eqn00242.gif]。（平面应力情况不使用。）
- ![](../graphics/ker_eqn00243.gif]。
- ![](../graphics/ker_eqn00244.gif]。
- ![](../graphics/ker_eqn00245.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=SHORT_FIBER，则没有表数据。

**返回值**

一个 Expansion 对象。

**异常**

RangeError。

### 60.49.2 成员

Expansion 对象的成员与 [Expansion](pt02ch60pyo49.md#ker-expansion-expansion-cpp) 方法的参数具有相同的名称和描述。

### 60.49.3 对应的分析关键字

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |
