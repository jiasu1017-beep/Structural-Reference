# 60.92 Solubility 对象

Solubility 对象用于指定溶解度。

**访问**

```
materialApi.materials()[*name*].solubility()
```

### 60.92.1 Solubility(...)

此方法创建一个 Solubility 对象。

**路径**

```
materialApi.materials()[*name*].Solubility
```

**原型**

```
odb_Solubility&
Solubility(const odb_SequenceSequenceDouble& table,
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

- 溶解度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Solubility 对象。

**异常**

RangeError。

### 60.92.2 成员

Solubility 对象的成员与 [Solubility](pt02ch60pyo92.md#ker-solubility-solubility-cpp) 方法的参数具有相同的名称和描述。

### 60.92.3 对应的分析关键字

| [*SOLUBILITY](../key/key-link.md#usb-kws-msolubility) |
| --- |
