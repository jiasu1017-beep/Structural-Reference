# 19.13 SpringDashpot 对象









SpringDashpot 对象是 [SpringDashpotToGround](pt01ch19pyo14.md) 和 [TwoPointSpringDashpot](pt01ch19pyo15.md) 对象的抽象基类型。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.13.1 resume()

此方法恢复先前被抑制的弹簧/阻尼器。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.13.2 suppress()

此方法抑制弹簧/阻尼器。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.13.3 成员

SpringDashpot 对象具有以下成员：

*name*

一个 String，指定存储库键。

*suppressed*

一个 Boolean，指定弹簧/阻尼器是否被抑制。默认值为 OFF。





