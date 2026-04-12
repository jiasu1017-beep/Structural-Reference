# 60.79 PorousBulkModuli 对象

PorousBulkModuli 对象用于定义土壤和岩石的体积模量。

**访问**

```
materialApi.materials()[*name*].porousBulkModuli()
```

### 60.79.1 PorousBulkModuli(...)

此方法创建一个 PorousBulkModuli 对象。

**路径**

```
materialApi.materials()[*name*].PorousBulkModuli
```

**原型**

```
odb_PorousBulkModuli&
PorousBulkModuli(const odb_SequenceSequenceDouble& table,
                 bool temperatureDependency);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

**表数据**

- 固体颗粒的体积模量。
- 渗透流体的体积模量。
- 温度（如果数据依赖温度）。

**返回值**

一个 PorousBulkModuli 对象。

**异常**

无。

### 60.79.2 成员

PorousBulkModuli 对象的成员与 [PorousBulkModuli](pt02ch60pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-cpp) 方法的参数具有相同的名称和描述。

### 60.79.3 对应的分析关键字

| [*POROUS BULK MODULI](../key/key-link.md#usb-kws-mporousbulkmod) |
| --- |
