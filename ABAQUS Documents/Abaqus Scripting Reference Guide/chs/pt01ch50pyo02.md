# 50.3 Control 对象

Control 对象用于提供额外的可选通用求解控制。

**访问**

```
import step
mdb.models[*name*].steps[*name*].control
```

### 50.3.1 setValues(...)

此方法修改 Control 对象。

**必需参数**

无。

**可选参数**

*allowPropagation*

一个布尔值，指定是否允许所有控制值从前一步传播。将此参数设置为 ON 会自动将 *resetDefaultValues* 设置为 OFF。默认值为 ON。

*resetDefaultValues*

一个布尔值，指定是否使用所有默认控制值。将此参数设置为 ON 会自动将 *allowPropagation* 设置为 OFF。默认值为 OFF。

*discontinuous*

一个布尔值，指定是否为具有严重不连续行为的分析设置通常可以提高效率的 *timeIncrementation* 值。默认值为 OFF。

*constraints*

SymbolicConstant DEFAULT 或一个 Float 序列，指定约束方程的容差。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*lineSearch*

SymbolicConstant DEFAULT 或一个 Float 序列，指定线性搜索控制参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*timeIncrementation*

SymbolicConstant DEFAULT 或一个 Float 序列，指定时间增量控制参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*directCyclic*

SymbolicConstant DEFAULT 或一个 Float 序列，指定直接循环控制参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*concentrationField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定质量浓度场平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*displacementField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定位移场和翘曲自由度场平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*electricalPotentialField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定电势场平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*globalField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定所有适用场平衡方程的参数。此参数将覆盖所有其他场平衡方程控制值。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*hydrostaticFluidPressureField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定静态流体元素体积约束参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*poreFluidPressureField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定孔隙液体积连续性平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*rotationField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定旋转场平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*temperatureField*

SymbolicConstant DEFAULT 或一个 Float 序列，指定温度场平衡方程参数。如果指定的序列包含值为 0 的元素，则该元素将被设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

*vcctLinearScaling*

SymbolicConstant DEFAULT 或一个 Float，指定 VCCT 分裂分析的线性缩放参数。如果指定值为 0，则将设置为其系统定义的值。该值也可以是 SymbolicConstant DEFAULT。默认值为 DEFAULT。

**返回值**

无

**异常**

RangeError。

### 50.3.2 成员

Control 对象具有与 [setValues](pt01ch50pyo03.md#ker-control-setvalues-pyc) 方法参数相同名称和描述的成员。
