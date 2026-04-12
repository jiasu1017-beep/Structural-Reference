# 3.1 Amplitude 对象





Amplitude 对象是其他 Amplitude 对象的抽象基类型。Amplitude 对象没有显式构造函数。Amplitude 对象的方法和成员对从 Amplitude 派生的所有对象都是通用的。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.1.1 成员

Amplitude 对象具有以下成员：

*name*

一个 String，指定仓库键。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。




