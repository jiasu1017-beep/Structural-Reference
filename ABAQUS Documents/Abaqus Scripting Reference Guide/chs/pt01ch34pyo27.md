# 34.27 SectionCategory 对象

SectionCategory 对象用于将具有相似截面的模型区域分组。具有相同数量截面点或积分点的截面定义被分组在一起。

要访问特定截面定义的数据，请使用输出数据库中的各个 [Section](pt01ch46pyo01.md) 对象。有关更多信息，请参阅第 8 章"梁截面轮廓命令"和第 46 章"截面命令"。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].elements[*i*].sectionCategory
session.odbs[*name*].parts[*name*].elementSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].parts[*name*].nodeSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].parts[*name*].surfaces[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.elementSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.nodeSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.surfaces[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].sectionCategories[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].elements[*i*].sectionCategory
```

### 34.27.1 SectionCategory(...)

此方法创建 SectionCategory 对象。

**路径**

```
session.odbs[*name*].SectionCategory
```

**必要参数**

*name*

一个字符串，指定类别名称。

*description*

一个字符串，指定类别描述。

**可选参数**

无。

**返回值**

SectionCategory 对象。

**异常**

无。

### 34.27.2 成员

SectionCategory 对象具有与 [SectionCategory](pt01ch34pyo27.md#ker-sectioncategory-sectioncategory-pyc) 方法的参数名称和描述相同的成员。

此外，SectionCategory 对象可以具有以下成员：

*sectionPoints*

一个 [SectionPointArray](pt01ch34pyo28.md) 对象。
