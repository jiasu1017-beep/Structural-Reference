# 60.63 Hysteresis 对象

Hysteresis 对象用于指定弹性体滞后行为材料模型的蠕变部分。

**访问**

```
materialApi.materials()[*name*].hyperelastic().hysteresis()
```

### 60.63.1 Hysteresis(...)

此方法创建一个 Hysteresis 对象。

**路径**

```
materialApi.materials()[*name*].hyperelastic().Hysteresis
```

**原型**

```
odb_Hysteresis&
Hysteresis(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 应力缩放因子。
- 蠕变参数。
- 有效应力指数。
- 蠕变应变指数。

**返回值**

一个 Hysteresis 对象。

**异常**

RangeError。

### 60.63.2 成员

Hysteresis 对象的成员与 [Hysteresis](pt02ch60pyo63.md#ker-hysteresis-hysteresis-cpp) 方法的参数具有相同的名称和描述。

### 60.63.3 对应的分析关键字

| [*HYSTERESIS](../key/key-link.md#usb-kws-mhysteresis) |
| --- |
