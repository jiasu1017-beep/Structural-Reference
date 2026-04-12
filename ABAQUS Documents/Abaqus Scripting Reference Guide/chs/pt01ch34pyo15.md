# 34.17 OdbMeshElement 对象

OdbMeshElement 对象使用 `part.addElements` 或 `rootAssembly.addElements` 方法创建。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].elementSets[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].nodeSets[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].surfaces[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.elements[*i*]
session.odbs[*name*].rootAssembly.elementSets[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.nodeSets[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.surfaces[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].elements[*i*]
```

### 34.17.1 成员

OdbMeshElement 对象可以具有以下成员：

*label*

一个整数，指定单元标签。

*type*

一个字符串，指定单元类型。

*sectionCategory*

一个 [SectionCategory](pt01ch34pyo27.md) 对象，指定单元截面属性。

*connectivity*

整数元组，指定单元连接性。对于连接到地面的连接器单元，另一个节点在连接数据中重复。地面节点的位置无法确定。这是一个限制。需要注意的是，这与 MDB 的 MeshElement 对象不同，后者连接性是节点索引而不是节点标签。

*instanceNames*

字符串元组，指定单元连接性中节点的实例名称。

*instanceName*

一个字符串，指定实例名称。
