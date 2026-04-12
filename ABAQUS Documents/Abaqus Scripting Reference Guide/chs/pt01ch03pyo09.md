# 3.9 PsdDefinition 对象





PsdDefinition 对象定义随机响应加载的交叉谱密度频率函数。

PsdDefinition 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.9.1 PsdDefinition(...)

此方法创建一个 PsdDefinition 对象。

**路径**

```
mdb.models[*name*].PsdDefinition
session.odbs[*name*].PsdDefinition
```

**必需参数**

*name*

一个 String，指定仓库键。

*data*

一个 Float 序列的序列，指定频率函数的实部、虚部以及取决于 *unitType* 的频率或频段编号值。

**可选参数**

*unitType*

一个 SymbolicConstant，指定用于指定频率函数的单位类型。FORCE 意味着功率单位。BASE 意味着用于定义基础运动的gravity。DB 意味着分贝单位。可能的值为 FORCE、BASE 和 DB。默认值为 FORCE。

*referenceGravityAcceleration*

一个 Float，指定参考重力加速度。当 *unitType* = BASE 时适用此参数。默认值为 1.0。

*referenecePower*

一个 Float，指定参考功率值，以载荷单位平方计。当 *unitType* = DB 时适用此参数。默认值为 0.0。

*user*

一个 Boolean，指定频率函数是否在用户子程序 UPSD 中定义。如果指定，则 *data* 不适用，且 *unitType* 值不能为 DB。默认值为 OFF。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

*amplitude*

一个 String，指定用于定义交叉谱密度频率函数的动态事件的幅度名称。默认值为空字符串。

**返回值**

一个 PsdDefinition 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.9.2 setValues(...)

此方法修改 PsdDefinition 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PsdDefinition](pt01ch03pyo09.md#ker-psddefinition-psddefinition-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.9.3 成员

PsdDefinition 对象具有与 [PsdDefinition](pt01ch03pyo09.md#ker-psddefinition-psddefinition-pyc) 方法参数相同名称和描述的成员。

### 3.9.4 对应分析关键字

| [*PSD-DEFINITION](../key/key-link.md#usb-kws-mpsddef) |
| --- |



