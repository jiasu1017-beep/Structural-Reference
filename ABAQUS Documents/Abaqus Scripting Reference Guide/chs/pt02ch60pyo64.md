# 60.64 InelasticHeatFraction 对象

InelasticHeatFraction 对象用于定义作为热源出现的非弹性耗散速率的分数。

**访问**

```
materialApi.materials()[*name*].inelasticHeatFraction()
```

### 60.64.1 InelasticHeatFraction(...)

此方法创建一个 InelasticHeatFraction 对象。

**路径**

```
materialApi.materials()[*name*].InelasticHeatFraction
```

**原型**

```
odb_InelasticHeatFraction&
InelasticHeatFraction(double fraction);
```

**必需参数**

无。

**可选参数**

*fraction*

一个 Double，指定作为单位体积热通量出现的非弹性耗散速率的分数。如果需要，该分数可能包括单位转换因子。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.9。

**返回值**

一个 InelasticHeatFraction 对象。

**异常**

RangeError。

### 60.64.2 成员

InelasticHeatFraction 对象的成员与 [InelasticHeatFraction](pt02ch60pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-cpp) 方法的参数具有相同的名称和描述。

### 60.64.3 对应的分析关键字

| [*INELASTIC HEAT FRACTION](../key/key-link.md#usb-kws-minelastheatfrac) |
| --- |
