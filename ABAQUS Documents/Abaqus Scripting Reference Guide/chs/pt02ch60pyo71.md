# 60.71 MoistureSwelling 对象

MoistureSwelling 对象用于定义湿气驱动的膨胀。

**访问**

```
materialApi.materials()[*name*].moistureSwelling()
```

### 60.71.1 MoistureSwelling(...)

此方法创建一个 MoistureSwelling 对象。

**路径**

```
materialApi.materials()[*name*].MoistureSwelling
```

**原型**

```
odb_MoistureSwelling&
MoistureSwelling(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 体积湿气膨胀应变，![](../graphics/ker_eqn00294.gif]。
- 饱和度，![](../graphics/ker_eqn00234.gif]。此值必须在范围 ![](../graphics/ker_eqn00295.gif) 内。

**返回值**

一个 MoistureSwelling 对象。

**异常**

无。

### 60.71.2 成员

MoistureSwelling 对象的成员与 [MoistureSwelling](pt02ch60pyo71.md#ker-moistureswelling-moistureswelling-cpp) 方法的参数具有相同的名称和描述。

此外，MoistureSwelling 对象可以具有以下成员：

**原型**

```
odb_Ratios ratios() const;
```

*ratios*

一个 [Ratios](pt02ch60pyo86.md) 对象。

### 60.71.3 对应的分析关键字

| [*MOISTURE SWELLING](../key/key-link.md#usb-kws-mmoistureswell) |
| --- |
