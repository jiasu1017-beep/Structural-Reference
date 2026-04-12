# 60.96 Swelling 对象

Swelling 对象用于指定材料的时变体积膨胀。

**访问**

```
materialApi.materials()[*name*].swelling()
```

### 60.96.1 Swelling(...)

此方法创建一个 Swelling 对象。

**路径**

```
materialApi.materials()[*name*].Swelling
```

**原型**

```
odb_Swelling&
Swelling(const odb_SequenceSequenceDouble& table,
         const odb_String& law,
         bool temperatureDependency,
         int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

此参数仅在 *law*="INPUT" 时有效。

**可选参数**

*law*

一个 odb_String，指定定义膨胀行为的数据类型。可能的值为"INPUT"和"USER"。默认值为"INPUT"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 体积膨胀应变率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Swelling 对象。

**异常**

RangeError。

### 60.96.2 成员

Swelling 对象的成员与 [Swelling](pt02ch60pyo96.md#ker-swelling-swelling-cpp) 方法的参数具有相同的名称和描述。

此外，Swelling 对象可以具有以下成员：

**原型**

```
odb_Ratios ratios() const;
```

*ratios*

一个 [Ratios](pt02ch60pyo86.md) 对象。

### 60.96.3 对应的分析关键字

| [*SWELLING](../key/key-link.md#usb-kws-mswelling) |
| --- |
