# 60.13 CastIronPlasticity 对象

CastIronPlasticity 对象用于指定铸铁塑性模型。

**访问**

```
materialApi.materials()[*name*].castIronPlasticity()
```

### 60.13.1 CastIronPlasticity(...)

此方法创建一个 CastIronPlasticity 对象。

**路径**

```
materialApi.materials()[*name*].CastIronPlasticity
```

**原型**

```
odb_CastIronPlasticity&
CastIronPlasticity(const odb_SequenceSequenceDouble& table,
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

表数据指定以下内容：
- 塑性泊松比，![](../graphics/ker_eqn00103.gif)（无量纲）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CastIronPlasticity 对象。

**异常**

RangeError。

### 60.13.2 成员

CastIronPlasticity 对象的成员与 [CastIronPlasticity](pt02ch60pyo13.md#ker-castironplasticity-castironplasticity-cpp) 方法的参数具有相同的名称和描述。

此外，CastIronPlasticity 对象可以具有以下成员：

**原型**

```
odb_CastIronTensionHardening castIronTensionHardening() const;
odb_CastIronCompressionHardening castIronCompressionHardening() const;
```

*castIronTensionHardening*

一个 [CastIronTensionHardening](pt02ch60pyo14.md) 对象。

*castIronCompressionHardening*

一个 [CastIronCompressionHardening](pt02ch60pyo12.md) 对象。

### 60.13.3 对应的分析关键字

| [*CAST IRON PLASTICITY](../key/key-link.md#usb-kws-mcastironplastic) |
| --- |
