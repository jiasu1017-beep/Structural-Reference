# 44.1 SectionAssignment 对象

SectionAssignment 对象用于在装配、零件或零件实例上指定截面分配。装配上的截面分配仅限用于连接器元素。

**访问**

```
import section
mdb.models[*name*].parts[*name*].sectionAssignments[*i*]
import assembly
mdb.models[*name*].rootAssembly.sectionAssignments[*i*]
import odbAccess
session.odbs[*name*].parts[*name*].sectionAssignments[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].sectionAssignments[*i*]
session.odbs[*name*].rootAssembly.sectionAssignments[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.sectionAssignments[*i*]
```

### 44.1.1 SectionAssignment(...)

此方法创建 SectionAssignment 对象。

**Path**

```
mdb.models[*name*].parts[*name*].SectionAssignment
```

```
mdb.models[*name*].rootAssembly.SectionAssignment
```

**必需参数**

*region*

 [Set](pt01ch45pyo04.md) 对象，指定要分配截面的区域。

*sectionName*

 String，指定截面的名称。

**可选参数**

*thicknessAssignment*

 SymbolicConstant，指定截面厚度分配方法。可选值为 FROM_SECTION 和 FROM_GEOMETRY。默认值为 FROM_SECTION。

*offset*

 Float，指定壳截面的偏移量。默认值为 0.0。

*offsetType*

 SymbolicConstant，指定用于定义壳偏移的方法。如果 *offsetType* 设置为 OFFSET_FIELD，则 *offsetField* 必须有值。可选值为 SINGLE_VALUE、MIDDLE_SURFACE、TOP_SURFACE、BOTTOM_SURFACE、FROM_GEOMETRY 和 OFFSET_FIELD。默认值为 SINGLE_VALUE。

*offsetField*

 String，指定偏移字段的名称。默认值为 ""。

**返回值**

SectionAssignment 对象。

**异常**

无。

### 44.1.2 resume()

此方法恢复先前被抑制的截面分配。

**参数**

无。

**返回值**

无

**异常**

无。

### 44.1.3 suppress()

此方法抑制截面分配。

**参数**

无。

**返回值**

无

**异常**

无。

### 44.1.4 getVertices(...)

此方法仅对连接器截面分配有效。此方法返回由连接器端点坐标元组组成的序列。

**参数**

无。

**返回值**

浮点数元组的序列。

**异常**

如果对任何截面分配（连接器截面分配除外）调用 getVertices()，则会抛出异常。

```
This method is valid only for connector section assignments.
```

无。

### 44.1.5 setValues(...)

此方法修改 SectionAssignment 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [SectionAssignment](pt01ch44pyo01.md#ker-sectionassignment-sectionassignment-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 44.1.6 成员

SectionAssignment 对象的成员与 [SectionAssignment](pt01ch44pyo01.md#ker-sectionassignment-sectionassignment-pyc) 方法的参数具有相同的名称和描述。

此外，SectionAssignment 对象具有以下成员：

*suppressed*

 Boolean，指定截面分配是否被抑制。默认值为 OFF。

