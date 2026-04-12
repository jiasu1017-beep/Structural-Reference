# 60.35 Damping 对象

Damping 对象用于指定材料阻尼。

**访问**

```
materialApi.materials()[*name*].damping()
```

### 60.35.1 Damping(...)

此方法创建一个 Damping 对象。

**路径**

```
materialApi.materials()[*name*].Damping
```

**原型**

```
odb_Damping&
Damping(double alpha,
        double beta,
        double composite,
        double structural);
```

**必需参数**

无。

**可选参数**

*alpha*

一个 Double，指定 ![](../graphics/ker_eqn00161.gif) 因子，用于在直接积分和显式动力学中创建质量比例阻尼。默认值为 0.0。

*beta*

一个 Double，指定 ![](../graphics/ker_eqn00162.gif) 因子，用于在直接积分和显式动力学中创建刚度比例阻尼。默认值为 0.0。

*composite*

一个 Double，指定临界阻尼分数，在计算模态复合阻尼因子时与该材料一起使用（用于模态动力学）。默认值为 0.0。

此参数仅适用于 Abaqus/Standard 分析。

*structural*

一个 Double，指定结构因子，用于在直接积分和显式动力学中创建材料阻尼。默认值为 0.0。

**返回值**

一个 Damping 对象。

**异常**

RangeError。

### 60.35.2 成员

Damping 对象的成员与 [Damping](pt02ch60pyo35.md#ker-damping-damping-cpp) 方法的参数具有相同的名称和描述。

### 60.35.3 对应的分析关键字

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |
