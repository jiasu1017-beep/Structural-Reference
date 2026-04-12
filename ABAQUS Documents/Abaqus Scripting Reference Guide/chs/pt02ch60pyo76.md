# 60.75 Piezoelectric 对象

Piezoelectric 对象用于指定压电材料属性。

**访问**

```
materialApi.materials()[*name*].piezoelectric()
```

### 60.75.1 Piezoelectric(...)

此方法创建一个 Piezoelectric 对象。

**路径**

```
materialApi.materials()[*name*].Piezoelectric
```

**原型**

```
odb_Piezoelectric&
Piezoelectric(const odb_SequenceSequenceDouble& table,
              const odb_String& type,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定压电属性的材料系数类型。可能的值为"STRAIN"和"STRESS"。默认值为"STRESS"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=STRESS，表数据指定以下内容：
- ![](../graphics/ker_eqn00297.gif]。
- ![](../graphics/ker_eqn00298.gif]。
- ![](../graphics/ker_eqn00299.gif]。
- ![](../graphics/ker_eqn00300.gif]。
- ![](../graphics/ker_eqn00301.gif]。
- ![](../graphics/ker_eqn00302.gif]。
- ![](../graphics/ker_eqn00303.gif]。
- ![](../graphics/ker_eqn00304.gif]。
- ![](../graphics/ker_eqn00305.gif]。
- ![](../graphics/ker_eqn00306.gif]。
- ![](../graphics/ker_eqn00307.gif]。
- ![](../graphics/ker_eqn00308.gif]。
- ![](../graphics/ker_eqn00309.gif]。
- ![](../graphics/ker_eqn00310.gif]。
- ![](../graphics/ker_eqn00311.gif]。
- ![](../graphics/ker_eqn00312.gif]。
- ![](../graphics/ker_eqn00313.gif]。
- ![](../graphics/ker_eqn00314.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=STRAIN，表数据指定以下内容：
- ![](../graphics/ker_eqn00315.gif]。
- ![](../graphics/ker_eqn00316.gif]。
- ![](../graphics/ker_eqn00317.gif]。
- ![](../graphics/ker_eqn00318.gif]。
- ![](../graphics/ker_eqn00319.gif]。
- ![](../graphics/ker_eqn00320.gif]。
- ![](../graphics/ker_eqn00321.gif]。
- ![](../graphics/ker_eqn00322.gif]。
- ![](../graphics/ker_eqn00323.gif]。
- ![](../graphics/ker_eqn00324.gif]。
- ![](../graphics/ker_eqn00325.gif]。
- ![](../graphics/ker_eqn00326.gif]。
- ![](../graphics/ker_eqn00327.gif]。
- ![](../graphics/ker_eqn00328.gif]。
- ![](../graphics/ker_eqn00329.gif]。
- ![](../graphics/ker_eqn00330.gif]。
- ![](../graphics/ker_eqn00331.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Piezoelectric 对象。

**异常**

无。

### 60.75.2 成员

Piezoelectric 对象的成员与 [Piezoelectric](pt02ch60pyo75.md#ker-piezoelectric-piezoelectric-cpp) 方法的参数具有相同的名称和描述。

### 60.75.3 对应的分析关键字

| [*PIEZOELECTRIC](../key/key-link.md#usb-kws-mpiezoelect) |
| --- |
