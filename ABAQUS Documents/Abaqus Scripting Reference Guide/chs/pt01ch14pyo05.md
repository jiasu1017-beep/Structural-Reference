# 15.1 Datum 对象

Datum 对象是其他 Datum 对象的抽象基类型。Datum 对象没有显式构造函数。Datum 对象的方法和成员是所有派生自 Datum 的对象共有的。

**访问权限**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].datums[*i*]
```

### 15.1.1 成员

Datum 对象没有成员。

