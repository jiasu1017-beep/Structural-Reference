# 50.16 SolverControl 对象

SolverControl 对象用于提供额外的可选求解器控制。

**访问**

```
import step
mdb.models[*name*].steps[*name*].solverControl
```

### 50.16.1 setValues(...)

此方法修改 SolverControl 对象。

**必需参数**

无。

**可选参数**

*allowPropagation*

一个布尔值，指定是否允许所有求解器控制值从前一步传播。将此参数设置为 ON 会自动将 *resetDefaultValues* 设置为 OFF。默认值为 ON。

*resetDefaultValues*

一个布尔值，指定是否使用所有默认求解器控制值。将此参数设置为 ON 会自动将 *allowPropagation* 设置为 OFF。默认值为 OFF。

*relativeTolerance*

SymbolicConstant DEFAULT 或一个 Float，指定域分解迭代求解器收敛的相对容差。默认值为 DEFAULT。

*maxIterations*

SymbolicConstant DEFAULT 或一个 Int，指定线性求解器迭代的最大次数。默认值为 DEFAULT。

*fillInLevel*

SymbolicConstant DEFAULT 或一个 Int，指定不完全 LU 分解的填充水平（仅适用于静力学和土壤分析）。默认值为 DEFAULT。

**返回值**

无

**异常**

RangeError。

### 50.16.2 成员

SolverControl 对象具有与 [setValues](pt01ch50pyo16.md#ker-solvercontrol-setvalues-pyc) 方法参数相同名称和描述的成员。
