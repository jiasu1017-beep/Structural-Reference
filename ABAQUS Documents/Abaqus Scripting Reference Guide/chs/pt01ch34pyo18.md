# 34.18 OdbMeshNode 对象

OdbMeshNode 对象使用 `part.addNodes` 方法创建。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].elementSets[*name*].nodes[*i*]
session.odbs[*name*].parts[*name*].nodes[*i*]
session.odbs[*name*].parts[*name*].nodeSets[*name*].nodes[*i*]
session.odbs[*name*].parts[*name*].surfaces[*name*].nodes[*i*]
session.odbs[*name*].rootAssembly.elementSets[*name*].nodes[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.nodes[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].nodes[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.nodes[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.nodes[*i*]
session.odbs[*name*].rootAssembly.nodes[*i*]
session.odbs[*name*].rootAssembly.nodeSets[*name*].nodes[*i*]
session.odbs[*name*].rootAssembly.surfaces[*name*].nodes[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].nodes[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodes[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].nodes[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].nodes[*i*]
```

### 34.18.1 成员

OdbMeshNode 对象具有以下成员：

*label*

一个整数，指定节点标签。

*coordinates*

浮点数元组，指定全局笛卡尔坐标系中的节点坐标。
