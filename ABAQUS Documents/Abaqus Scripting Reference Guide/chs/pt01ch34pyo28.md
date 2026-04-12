# 34.28 SectionPoint 对象

SectionPoint 对象描述截面类别内截面点的位置。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].elements[*i*].sectionCategory\
.sectionPoints[*i*]
session.odbs[*name*].parts[*name*].elementSets[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].parts[*name*].nodeSets[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].parts[*name*].surfaces[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.elements[*i*].sectionCategory\
.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.elementSets[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.nodeSets[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].rootAssembly.surfaces[*name*].elements[*i*]\
.sectionCategory.sectionPoints[*i*]
session.odbs[*name*].sectionCategories[*name*].sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*]\
.locations[*i*].sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].elements[*i*].sectionCategory\
.sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].elements[*i*].sectionCategory.sectionPoints[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.sectionPoint
```

### 34.28.1 SectionPoint(...)

此方法创建 SectionPoint 对象。

**路径**

```
session.odbs[*name*].sectionCategories[*name*].SectionPoint
```

**必要参数**

*number*

一个整数，指定截面点的编号。有关编号约定，请参阅《Abaqus Analysis User's Guide》第 29.3 节"梁单元"和第 29.6 节"壳单元"。

*description*

一个字符串，指定截面点的描述。

**可选参数**

无。

**返回值**

SectionPoint 对象。

**异常**

无。

### 34.28.2 成员

SectionPoint 对象具有与 [SectionPoint](pt01ch34pyo28.md#ker-sectionpoint-sectionpoint-pyc) 方法的参数名称和描述相同的成员。
