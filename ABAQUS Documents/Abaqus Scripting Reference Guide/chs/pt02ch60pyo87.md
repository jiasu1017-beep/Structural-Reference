# 60.87 Regularization 对象

Regularization 对象用于定义用于正则化材料数据的容差。

**访问**

```
materialApi.materials()[*name*].regularization()
```

### 60.87.1 Regularization(...)

此方法创建一个 Regularization 对象。

**路径**

```
materialApi.materials()[*name*].Regularization
```

**原型**

```
odb_Regularization&
Regularization(double rtol,
               const odb_String& strainRateRegularization);
```

**必需参数**

无。

**可选参数**

*rtol*

一个 Double，指定用于正则化材料数据的容差。默认值为 0.03。

*strainRateRegularization*

一个 odb_String，指定应变率相关材料数据正则化的形式。可能的值为"LOGARITHMIC"和"LINEAR"。默认值为"LOGARITHMIC"。

**返回值**

一个 Regularization 对象。

**异常**

RangeError。

### 60.87.2 成员

Regularization 对象的成员与 [Regularization](pt02ch60pyo87.md#ker-regularization-regularization-cpp) 方法的参数具有相同的名称和描述。

### 60.87.3 对应的分析关键字

| [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |
