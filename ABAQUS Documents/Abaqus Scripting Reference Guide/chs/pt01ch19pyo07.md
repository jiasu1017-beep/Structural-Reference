# 19.7 Fastener 对象









Fastener 对象是 [PointFastener](pt01ch19pyo11.md)、[DiscreteFastener](pt01ch19pyo06.md) 和 [AssembledFastener](pt01ch19pyo02.md) 的抽象基类型。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.7.1 resume()

此方法恢复先前被抑制的紧固件。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.7.2 suppress()

此方法抑制紧固件。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.7.3 成员

Fastener 对象具有以下成员：

*name*

一个 String，指定存储库键。

*suppressed*

一个 Boolean，指定紧固件是否被抑制。默认值为 OFF。





