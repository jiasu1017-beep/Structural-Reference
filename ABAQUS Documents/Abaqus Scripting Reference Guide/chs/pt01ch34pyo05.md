# 34.5 FieldLocation 对象

FieldLocation 对象指定字段中数据可用的位置。例如，位移场将具有 *position* 成员值为 NODAL 的 FieldLocation 对象。FieldLocation 对象没有构造函数；当通过 [FieldOutput](pt01ch34pyo06.md) 对象的 `addData` 方法将数据添加到 [FieldOutput](pt01ch34pyo06.md) 对象时，它会自动创建作为其 *location* 成员的元素的 FieldLocation 对象。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*]\
.locations[*i*]
```

### 34.5.1 成员

FieldLocation 对象可以具有以下成员：

*position*

一个 SymbolicConstant，指定输出在元素中的位置。可能的值为：
- NODAL，指定在节点处计算的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- ELEMENT_FACE。
- CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*sectionPoints*

一个 [SectionPointArray](pt01ch34pyo28.md) 对象。
