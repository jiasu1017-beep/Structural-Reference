# 2.10 Model 对象





以下命令对 Model 对象进行操作。有关 Model 对象的更多信息，请参见["Model 对象"，第 33.1 节](pt01ch33pyo01.md)。

**访问**

```
import mesh
```

### 2.10.1 adaptiveRemesh(...)

此方法使用模型中活动的重网格规则和先前分析中的误差指示器结果对模型进行重网格划分。

**必需参数**

*odb*

一个 [Odb](pt01ch34pyo01.md) 对象，包含误差输出场结果。

**可选参数**

无。

**返回值**

一个 [AdaptivityIteration](pt01ch02pyo05.md) 对象。

**异常**

无。




