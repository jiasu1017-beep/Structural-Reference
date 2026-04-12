# 7.13 ReferencePoint 对象

ReferencePoint 对象没有直接构造函数；当创建 [Feature](pt01ch20pyo01.md) 对象时会创建它。`ReferencePoint` 方法创建一个 [Feature](pt01ch20pyo01.md) 对象，该对象创建一个 ReferencePoint 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].referencePoints[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].referencePoints[*i*]
mdb.models[*name*].parts[*name*].referencePoints[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].referencePoints[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.referencePoints[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*]\
.referencePoints[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].referencePoints[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].referencePoints[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].referencePoints[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*]\
.referencePoints[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].referencePoints[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*]\
.referencePoints[*i*]
mdb.models[*name*].rootAssembly.referencePoints[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].referencePoints[*i*]
```

### 7.13.1 成员

ReferencePoint 对象没有成员。
