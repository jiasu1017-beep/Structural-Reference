# 60.80 PorousElastic 对象

PorousElastic 对象用于指定多孔材料的弹性材料属性。

**访问**

```
materialApi.materials()[*name*].porousElastic()
```

### 60.80.1 PorousElastic(...)

此方法创建一个 PorousElastic 对象。

**路径**

```
materialApi.materials()[*name*].PorousElastic
```

**原型**

```
odb_PorousElastic&
PorousElastic(const odb_SequenceSequenceDouble& table,
              const odb_String& shear,
              bool temperatureDependency,
              int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*shear*

一个 odb_String，指定剪切定义形式。可能的值为"G"和"POISSON"。默认值为"POISSON"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *shear*=G，表数据指定以下内容：
- 对数体积模量，![](../graphics/ker_eqn00342.gif]。（无量纲。）
- 剪切模量，![](../graphics/ker_eqn00182.gif]。
- 弹性拉伸极限，![](../graphics/ker_eqn00343.gif。（此值不能为负。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *shear*=POISSON，表数据指定以下内容：
- 对数体积模量，![](../graphics/ker_eqn00342.gif]。（无量纲。）
- 泊松比，![](../graphics/ker_eqn00164.gif]。
- 弹性拉伸极限，![](../graphics/ker_eqn00343.gif。（此值不能为负。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 PorousElastic 对象。

**异常**

RangeError。

### 60.80.2 成员

PorousElastic 对象的成员与 [PorousElastic](pt02ch60pyo80.md#ker-porouselastic-porouselastic-cpp) 方法的参数具有相同的名称和描述。

### 60.80.3 对应的分析关键字

| [*POROUS ELASTIC](../key/key-link.md#usb-kws-mporouselastic) |
| --- |
