# 61.18 OdbMeshElement 对象

OdbMeshElement 对象使用 `part.addElements` 或 `rootAssembly.addElements` 方法创建。

**访问**

```
odb.parts()[*name*].elements(*i*)
odb.parts()[*name*].elementSets()[*name*].elements(*i*)
odb.parts()[*name*].nodeSets()[*name*].elements(*i*)
odb.parts()[*name*].surfaces()[*name*].elements(*i*)
odb.rootAssembly().elements(*i*)
odb.rootAssembly().elementSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)
odb.rootAssembly().nodeSets()[*name*].elements(*i*)
odb.rootAssembly().surfaces()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*)
```

### 61.18.1 成员

OdbMeshElement 对象可以具有以下成员：

**原型**

```
int label() const;
               const int* connectivity(int& numNodes) const ;
               odb_SequenceInt connectivity() const;
               odb_SectionCategory sectionCategory() const;
               odb_String type() const;
               odb_String instanceName() const;
               odb_SequenceString instanceNames() const;
```

*label*

一个 Int，指定元素标签。

*type*

一个 odb_String，指定元素类型。

*sectionCategory*

一个 [SectionCategory](pt02ch61pyo27.md) 对象，指定元素截面属性。

*connectivity*

一个指向 Int 数组的指针，指定元素连通性。对于连接到地面的连接器元素，另一个节点在连通性数据中重复。无法确定地面节点的位置。这是一个限制。需要注意它与 MDB 的 MeshElement 对象的区别，后者的连通性是节点索引而不是节点标签。

*instanceNames*

一个指向 String 数组的指针，指定元素连通性中节点的实例名称。

*instanceName*

一个 odb_String，指定实例名称。
