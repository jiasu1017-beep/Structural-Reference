# 36.2 CombinedTermDesignResponse 对象

CombinedTermDesignResponse 对象定义组合项设计响应。

CombinedTermDesignResponse 对象派生自 [DesignResponse](pt01ch36pyo04.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].designResponses[*name*]
```

### 36.2.1 CombinedTermDesignResponse(...)

此方法创建 CombinedTermDesignResponse 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].CombinedTermDesignResponse
```

**必要参数**

*name*

一个字符串，指定设计响应仓库键。

*terms*

字符串序列，指定要组合的设计响应名称。

**可选参数**

*filterMaxRadius*

`None` 或浮点数序列，指定当 *method* 为 FILTER 时使用的最大影响半径。默认值为 `None`。

*filterExponent*

一个 Float，指定当 *method* 为 FILTER 时使用的指数。默认值为 1.0。

*filterRadiusReduction*

一个 Float，指定当 *method* 为 FILTER 时使用的取决于表面弯曲的半径减少。默认值为 0.2。

*highCutOff*

`None` 或浮点数序列，指定当 *method* 为 CUT_OFF 时使用的向量值的上限。所有大于 *highCutOff* 的值都设置为 *highCutOff* 值。默认值为 `None`。

*lowCutOff*

一个 Float，指定当 *method* 为 CUT_OFF 时使用的向量值的下限。所有小于 *lowCutOff* 的值被视为 0。默认值为 0.0。

*method*

一个 SymbolicConstant，指定用于组合所选设计响应的方法。可能的值为：
- ABSOLUTE_DIFFERENCE
- ABSOLUTE_VALUE
- ADD
- COSINE
- CUT_OFF
- DELTA_OVER_1_ITERATION
- DELTA_OVER_2_ITERATIONS
- DELTA_OVER_3_ITERATIONS
- DELTA_OVER_4_ITERATIONS
- DELTA_OVER_5_ITERATIONS
- DELTA_OVER_6_ITERATIONS
- DIVIDE
- EXPONENTIAL
- FILTER
- INTEGER
- LOG
- MAXIMUM
- MINIMUM
- MULTIPLY
- NATURAL_LOG
- NEAREST_INTEGER
- NORM
- NORM_FIRST
- NTH_POWER
- NTH_ROOT
- SIGN
- SINE
- SQUARE_ROOT
- SUBTRACT
- TANGENT
- WEIGHTED_ADD

默认值为 ADD。

*weights*

浮点数序列，指定当 *method* 为 WEIGHTED_ADD 时应用于设计响应列表的权重。默认值为空序列。

**返回值**

CombinedTermDesignResponse 对象。

**异常**

无。

### 36.2.2 setValues(...)

此方法修改 CombinedTermDesignResponse 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [CombinedTermDesignResponse](pt01ch36pyo02.md#ker-combinedtermdesignresponse-combinedtermdesignrespons-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.2.3 成员

CombinedTermDesignResponse 对象具有与 [CombinedTermDesignResponse](pt01ch36pyo02.md#ker-combinedtermdesignresponse-combinedtermdesignrespons-pyc) 方法的参数名称和描述相同的成员。
