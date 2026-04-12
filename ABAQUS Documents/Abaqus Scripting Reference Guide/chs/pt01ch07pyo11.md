# 7.11 InterestingPoint 对象

有趣点可以位于以下位置：
- 边缘的中点。
- 圆弧的中点。
- 圆弧的中心。

InterestingPoint 对象是一个临时对象，不能从 [Mdb](pt01ch30pyo01.md) 对象访问。

**访问**

```
import part
import assembly
```

### 7.11.1 InterestingPoint(...)

此方法在边缘上创建一个有趣点。InterestingPoint 是一个临时对象。

**路径**

```
mdb.models[*name*].parts[*name*].InterestingPoint
```

```
mdb.models[*name*].rootAssembly.instances[*name*].InterestingPoint
```

**必需参数**

*edge*

一个 Edge 对象，指定有趣点所在的边缘。

*rule*

一个 SymbolicConstant，指定有趣点的位置。可能的值为 MIDDLE 或 CENTER。

**可选参数**

无。

**返回值**

一个 InterestingPoint 对象。

**异常**

无。

### 7.11.2 成员

InterestingPoint 对象没有成员。
