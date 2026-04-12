# 56.8 PsdDefinition 对象







PsdDefinition 对象定义随机响应加载的交叉谱密度频率函数。

PsdDefinition 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
Api.amplitudes()[*name*]
```

### 56.8.1 PsdDefinition(...)

此方法创建 PsdDefinition 对象。

**路径**

```
Api.PsdDefinition
```

**原型**

```
odb_PsdDefinition&
PsdDefinition(const odb_String& name,
              const odb_SequenceSequenceDouble& data,
              const odb_String& unitType,
              double referenceGravityAcceleration,
              double referenecePower,
              bool user,
              const odb_String& timeSpan,
              const odb_String& amplitude);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*data*

一个 odb_SequenceSequenceDouble，指定频率函数的实部、频率函数的虚部以及频率或频带号值，具体取决于 *unitType* 的值。

**可选参数**

*unitType*

一个 odb_String，指定指定频率函数的单位类型。"FORCE" 意味着功率单位。"BASE" 意味着用于定义基础运动的引力。"DB" 意味着分贝单位。可能的值为 "FORCE"、"BASE" 和 "DB"。默认值为 "FORCE"。

*referenceGravityAcceleration*

一个 Double，指定参考重力加速度。当 *unitType* = "BASE" 时应用此参数。默认值为 1.0。

*referenecePower*

一个 Double，指定参考功率值（负载单位平方）。当 *unitType* = "DB" 时应用此参数。默认值为 0.0。

*user*

一个 Boolean，指定频率函数是否在用户子程序 UPSD 中定义。如果指定，则 *data* 不适用，且 *unitType* 值不能为 "DB"。默认值为 false。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

*amplitude*

一个 odb_String，指定用于定义交叉谱密度频率函数的动态事件的幅值名称。默认值为空字符串。

**返回值**

PsdDefinition 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.8.2 setValues(...)

此方法修改 PsdDefinition 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [PsdDefinition](pt02ch56pyo08.md#ker-psddefinition-psddefinition-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.8.3 成员

PsdDefinition 对象具有与 [PsdDefinition](pt02ch56pyo08.md#ker-psddefinition-psddefinition-cpp) 方法的参数具有相同名称和描述的成员。

### 56.8.4 对应的分析关键字

| [*PSD-DEFINITION](../key/key-link.md#usb-kws-mpsddef) |
| --- |

