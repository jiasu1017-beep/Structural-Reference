# 60.98 TensionStiffening 对象

TensionStiffening 对象用于定义 [Concrete](pt02ch60pyo18.md) 模型中裂纹法向保留的拉伸应力。

**访问**

```
materialApi.materials()[*name*].concrete().tensionStiffening()
```

### 60.98.1 TensionStiffening(...)

此方法创建一个 TensionStiffening 对象。

**路径**

```
materialApi.materials()[*name*].concrete().TensionStiffening
```

**原型**

```
odb_TensionStiffening&
TensionStiffening(const odb_SequenceSequenceDouble& table,
                  const odb_String& type,
                  bool temperatureDependency,
                  int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*type*

一个 odb_String，指定开裂后行为如何定义。可能的值为"DISPLACEMENT"和"STRAIN"。默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=STRAIN，表数据指定以下内容：
- 剩余应力与开裂时应力的比值。
- 直接应变减去开裂时直接应变的绝对值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表数据指定以下内容：
- 开裂后线性强度损失为零应力时的位移，![](../graphics/ker_eqn00372.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 TensionStiffening 对象。

**异常**

RangeError。

### 60.98.2 成员

TensionStiffening 对象的成员与 [TensionStiffening](pt02ch60pyo98.md#ker-tensionstiffening-tensionstiffening-cpp) 方法的参数具有相同的名称和描述。

### 60.98.3 对应的分析关键字

| [*TENSION STIFFENING](../key/key-link.md#usb-kws-mtensionstiff) |
| --- |
