# 2.4 AdaptiveMeshDomain 对象





AdaptiveMeshDomain 对象定义控制任意拉格朗日欧拉（ALE）样式自适应平滑网格域的区域和控制。

**访问**

```
import step
mdb.models[*name*].steps[*name*].adaptiveMeshDomains[*name*]
```

### 2.4.1 AdaptiveMeshDomain(...)

此方法创建一个 AdaptiveMeshDomain 对象。

**路径**

```
mdb.models[*name*].steps[*name*].AdaptiveMeshDomain
```

**必需参数**

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用自适应网格域的区域。

**可选参数**

*controls*

一个 String，指定 [AdaptiveMeshControl](pt01ch02pyo03.md) 对象的名称。

*frequency*

一个 Int，指定执行自适应网格划分的增量频率。默认值为 10。

*initialMeshSweeps*

一个 Int，指定在此自适应网格定义处于活动状态的第一个步骤开始时执行的网格扫描次数。默认值为 5。

*meshSweeps*

一个 Int，指定在每个自适应网格增量中执行的网格扫描次数。默认值为 1。

**返回值**

一个 AdaptiveMeshDomain 对象。

**异常**

RangeError。

### 2.4.2 setValues(...)

此方法修改 AdaptiveMeshDomain 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AdaptiveMeshDomain](pt01ch02pyo04.md#ker-adaptivemeshdomain-adaptivemeshdomain-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 2.4.3 成员

AdaptiveMeshDomain 对象具有与 [AdaptiveMeshDomain](pt01ch02pyo04.md#ker-adaptivemeshdomain-adaptivemeshdomain-pyc) 方法参数相同名称和描述的成员。





