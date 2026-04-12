# 28.1 LoadCase 对象





LoadCase 对象用于定义构成特定加载条件以及承受该加载条件的结构线性响应的载荷和约束。

**访问**

```
import step
mdb.models[*name*].steps[*name*].loadCases[*name*]
```

### 28.1.1 LoadCase(...)

此方法在某个步骤中创建负载情形。

**路径**

```
mdb.models[*name*].steps[*name*].LoadCase
```

**必需参数**

*name*

一个 String，指定对象的名称。

**可选参数**

*boundaryConditions*

一个 (String, Float) 序列的序列，指定边界条件名称，后跟非零 Float 缩放因子。默认值为空序列。

*loads*

一个 (String, Float) 序列的序列，指定载荷名称，后跟非零 Float 缩放因子。默认值为空序列。

*includeActiveBaseStateBC*

一个 Boolean，指定是否包含从基态传播或修改的所有活动边界条件。默认值为 ON。

**返回值**

一个 LoadCase 对象。

**异常**

RangeError。

### 28.1.2 resume()

此方法恢复先前抑制的负载情形。

**参数**

无。

**返回值**

无

**异常**

无。

### 28.1.3 suppress()

此方法抑制负载情形。

**参数**

无。

**返回值**

无

**异常**

无。

### 28.1.4 setValues(...)

此方法修改 LoadCase 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [LoadCase](pt01ch28pyo01.md#ker-loadcase-loadcase-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 28.1.5 成员

LoadCase 对象具有与 [LoadCase](pt01ch28pyo01.md#ker-loadcase-loadcase-pyc) 方法参数同名的成员，描述也相同。

此外，LoadCase 对象具有以下成员：

*suppressed*

一个 Boolean，指定负载情形是否被抑制。默认值为 OFF。




