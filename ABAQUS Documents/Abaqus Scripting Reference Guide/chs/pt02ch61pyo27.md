# 61.27 SectionCategory 对象

SectionCategory 对象用于将模型中具有相似截面的区域分组。具有相同数量截面点或积分点的截面定义被分组在一起。

要访问特定截面定义的数据，请使用输出数据库中的各个 [Section](pt02ch63pyo01.md) 对象。有关更多信息，请参阅"第 8 章，'梁截面轮廓命令'"（[pt01ch08.md](pt01ch08.md)）和"第 46 章，'截面命令'"（[pt01ch46.md](pt01ch46.md)）。

**访问**

```
odb.parts()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].elementSets()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].nodeSets()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].surfaces()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().elements(*i*).sectionCategory()
odb.rootAssembly().elementSets()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().instances()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().nodeSets()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().surfaces()[*name*].elements(*i*).sectionCategory()
odb.sectionCategories()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*).sectionCategory()
```

### 61.27.1 SectionCategory(...)

此方法创建一个 SectionCategory 对象。

**路径**

```
odb.SectionCategory
```

**原型**

```
odb_SectionCategory&
SectionCategory(const odb_String& name,
                const odb_String& description);
```

**必需参数**

*name*

一个 odb_String，指定类别名称。

*description*

一个 odb_String，指定类别描述。

**可选参数**

无。

**返回值**

一个 SectionCategory 对象。

**异常**

无。

### 61.27.2 成员

SectionCategory 对象具有与 [SectionCategory](pt02ch61pyo27.md#ker-sectioncategory-sectioncategory-cpp) 方法参数相同名称和描述的成员。

此外，SectionCategory 对象可以具有以下成员：

**原型**

```
odb_String name() const;
odb_String description() const;
const odb_SectionPoint& sectionPoints(int index) const;
const odb_SequenceSectionPoint& sectionPoints() const;
```

*sectionPoints*

[SectionPoint](pt02ch61pyo28.md) 对象的序列。
