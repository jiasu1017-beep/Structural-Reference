# 60.65 JouleHeatFraction 对象

JouleHeatFraction 对象用于定义作为热量释放的电能的分数。

**访问**

```
materialApi.materials()[*name*].jouleHeatFraction()
```

### 60.65.1 JouleHeatFraction(...)

此方法创建一个 JouleHeatFraction 对象。

**路径**

```
materialApi.materials()[*name*].JouleHeatFraction
```

**原型**

```
odb_JouleHeatFraction&
JouleHeatFraction(double fraction);
```

**必需参数**

无。

**可选参数**

*fraction*

一个 Double，指定作为热量释放的电能的分数，包括任何单位转换因子。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 1.0。

**返回值**

一个 JouleHeatFraction 对象。

**异常**

RangeError。

### 60.65.2 成员

JouleHeatFraction 对象的成员与 [JouleHeatFraction](pt02ch60pyo65.md#ker-jouleheatfraction-jouleheatfraction-cpp) 方法的参数具有相同的名称和描述。

### 60.65.3 对应的分析关键字

| [*JOULE HEAT FRACTION](../key/key-link.md#usb-kws-mjouleheatfrac) |
| --- |
