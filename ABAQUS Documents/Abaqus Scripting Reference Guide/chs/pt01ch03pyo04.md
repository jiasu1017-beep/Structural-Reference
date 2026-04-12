# 3.4 Correlation 对象





Correlation 是一个对象，用于定义随机加载的交叉相关的部分。

Correlation 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*].correlation[*i*]
```

### 3.4.1 成员

Correlation 对象具有以下成员：

*name*

一个 String，指定仓库键。

*approach*

一个 SymbolicConstant，指定相关性数据表示中使用的方法。可能的值为 CORRELATED、MOVING_NOISE、UNCORRELATED 和 USER。默认值为 CORRELATED。

*data*

一个 Float 元组的元组，指定缩放因子的实部和虚部。如果 *approach*=MOVING_NOISE，则 *data* 表示噪声速度分量 1、2 和 3。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。




