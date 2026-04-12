# 25.68 StdStabilization 对象

StdStabilization 对象与 Abaqus/Standard 分析中的 [ContactStd](pt01ch25pyo24.md) 结合使用来指定接触稳定化。

StdStabilization 对象派生自 [ContactStabilization](pt01ch25pyo23.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].contactStabilizations[*name*]
```

### 25.68.1 StdStabilization(...)

此方法创建一个 StdStabilization 对象。

**路径**

```
mdb.models[*name*].StdStabilization
```

**必需参数**

*name*

字符串，指定接触稳定化存储库键。

**可选参数**

*zeroDistance*

 `None` 或浮点数，指定稳定化变为零的间隙距离。默认值为 `None`。

*reductionFactor*

浮点数，指定分析每增量减少接触稳定化系数的因子。默认值为 0.1。

*scaleFactor*

浮点数，指定分析缩放接触稳定化系数的因子。默认值为 1.0。

*tangentialFactor*

浮点数，指定在切向方向上缩放接触稳定化系数的因子。默认值为 0.0。

*amplitude*

字符串，指定定义接触稳定化在步骤上随时间变化的比例因子的 [Amplitude](pt01ch03pyo01.md) 对象的名称。默认值为空字符串。

*reset*

布尔值，指定是否取消在先前步骤中出现的使用非默认幅值涉及的接触稳定化规范的影响。默认值为 OFF。

**返回值**

StdStabilization 对象。

**异常**

RangeError。

### 25.68.2 setValues(...)

此方法修改 StdStabilization 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [StdStabilization](pt01ch25pyo68.md#ker-stdstabilization-stdstabilization-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 25.68.3 成员

StdStabilization 对象的成员与 [StdStabilization](pt01ch25pyo68.md#ker-stdstabilization-stdstabilization-pyc) 方法的参数具有相同的名称和描述。

### 25.68.4 对应的分析关键字

| [*CONTACT STABILIZATION](../key/key-link.md#usb-kws-hcontactstab) |
| --- |



