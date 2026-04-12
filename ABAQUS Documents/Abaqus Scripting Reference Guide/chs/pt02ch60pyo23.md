# 60.23 ConcreteTensionStiffening 对象

ConcreteTensionStiffening 对象用于指定混凝土损伤塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteTensionStiffening()
```

### 60.23.1 ConcreteTensionStiffening(...)

此方法创建一个 ConcreteTensionStiffening 对象。

**路径**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteTensionStiffening
```

**原型**

```
odb_ConcreteTensionStiffening&
ConcreteTensionStiffening(const odb_SequenceSequenceDouble& table,
                          bool rate,
                          const odb_String& type,
                          bool temperatureDependency,
                          int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*rate*

一个布尔值，指定数据是否依赖速率。默认值为 false。

*type*

一个 odb_String，指定后断裂行为数据的类型。可能的值为：
- "STRAIN"，指定后失效应力作为裂缝应变的函数。
- "DISPLACEMENT"，指定后失效应力作为裂缝位移的函数。
- "GFI"，指定失效应力作为断裂能的函数。

默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=STRAIN，表数据指定以下内容：
- 断裂后的剩余直接应力，![](../graphics/ker_eqn00104.gif)。
- 直接裂缝应变，![](../graphics/ker_eqn00137.gif)。
- 直接裂缝应变率，![](../graphics/ker_eqn00139.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表数据指定以下内容：
- 断裂后的剩余直接应力，![](../graphics/ker_eqn00104.gif)。
- 直接裂缝位移，![](../graphics/ker_eqn00138.gif)。
- 直接裂缝位移率，![](../graphics/ker_eqn00140.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=GFI，表数据指定以下内容：
- 失效应力，![](../graphics/ker_eqn00141.gif)。
- 断裂能，![](../graphics/ker_eqn00142.gif)。
- 直接裂缝位移率，![](../graphics/ker_eqn00140.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteTensionStiffening 对象。

**异常**

RangeError。

### 60.23.2 成员

ConcreteTensionStiffening 对象的成员与 [ConcreteTensionStiffening](pt02ch60pyo23.md#ker-concretetensionstiffening-concretetensionstiffening-cpp) 方法的参数具有相同的名称和描述。

### 60.23.3 对应的分析关键字

| [*CONCRETE TENSION STIFFENING](../key/key-link.md#usb-kws-mconcretetensstiff) |
| --- |
