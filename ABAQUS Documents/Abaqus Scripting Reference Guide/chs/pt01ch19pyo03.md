# 19.4 Crack 对象









Crack 对象是 [ContourIntegral](pt01ch19pyo03.md) 和未来裂缝对象的抽象基类型。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.4.1 resume()

此方法恢复先前被抑制的裂缝。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.4.2 suppress()

此方法抑制裂缝。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.4.3 成员

Crack 对象具有以下成员：

*name*

一个 String，指定存储库键。

*suppressed*

一个 Boolean，指定裂缝是否被抑制。默认值为 OFF。





