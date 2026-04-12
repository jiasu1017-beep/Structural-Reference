# 61.6 FieldLocation 对象





FieldLocation 对象指定场中数据可用的位置。例如，位移场将有一个 *position* 成员值为 NODAL 的 FieldLocation 对象。FieldLocation 对象没有构造函数；它是由 [FieldOutput](pt02ch61pyo07.md) 对象的 `addData` 方法自动创建的，作为 [FieldOutput](pt02ch61pyo07.md) 对象的 *location* 成员的元创建。

**访问**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].locations(*i*)
```

### 61.6.1 成员

FieldLocation 对象可以具有以下成员：

**原型**

```
odb_Enum::odb_ResultPositionEnum position() const;
const odb_SequenceSectionPoint& sectionPoints() const;
const odb_SectionPoint& sectionPoints(int index) const;
```

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定输出在元素中的位置。可能的值为：
- odb_Enum::NODAL，指定在节点处计算的值。
- odb_Enum::INTEGRATION_POINT，指定在积分点处计算的值。
- odb_Enum::ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- odb_Enum::ELEMENT_FACE。
- odb_Enum::CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*sectionPoints*

[SectionPoint](pt02ch61pyo28.md) 对象的序列。





