# 61.19 OdbMeshNode 对象

OdbMeshNode 对象使用 `part.addNodes` 方法创建。

**访问**

```
odb.parts()[*name*].elementSets()[*name*].nodes(*i*)
odb.parts()[*name*].nodes(*i*)
odb.parts()[*name*].nodeSets()[*name*].nodes(*i*)
odb.parts()[*name*].surfaces()[*name*].nodes(*i*)
odb.rootAssembly().elementSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].nodes(*i*)
odb.rootAssembly().nodes(*i*)
odb.rootAssembly().nodeSets()[*name*].nodes(*i*)
odb.rootAssembly().surfaces()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].nodes(*i*)
```

### 61.19.1 成员

OdbMeshNode 对象具有以下成员：

**原型**

```
int label() const;
const float* coordinates() const;
```

*label*

一个 Int，指定节点标签。

*coordinates*

一个指向 Float 数组的指针，指定全局 Cartesian 坐标系中的节点坐标。
