# 61.28 SectionPoint 对象

SectionPoint 对象描述截面类别内截面点位置。

**访问**

```
odb.parts()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.parts()[*name*].elementSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.parts()[*name*].nodeSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.parts()[*name*].surfaces()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().elements(*i*).sectionCategory().sectionPoints(*i*)
odb.rootAssembly().elementSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().nodeSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().surfaces()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.sectionCategories()[*name*].sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].locations(*i*)\
.sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).sectionPoint()
```

### 61.28.1 SectionPoint(...)

此方法创建一个 SectionPoint 对象。

**路径**

```
odb.sectionCategories()[*name*].SectionPoint
```

**原型**

```
odb_SectionPoint&
SectionPoint(int number,
             const odb_String& description);
```

**必需参数**

*number*

一个 Int，指定截面点的编号。关于编号约定，请参阅"Abaqus Analysis User's Guide"的"梁单元"第 29.3 节（[../usb/usb-link.md#usbebeam](../usb/usb-link.md#usbebeam)）和"壳单元"第 29.6 节（[../usb/usb-link.md#usbeshell](../usb/usb-link.md#usbeshell)）。

*description*

一个 odb_String，指定截面点的描述。

**可选参数**

无。

**返回值**

一个 SectionPoint 对象。

**异常**

无。

### 61.28.2 成员

SectionPoint 对象具有与 [SectionPoint](pt02ch61pyo28.md#ker-sectionpoint-sectionpoint-cpp) 方法参数相同名称和描述的成员。

**原型**

```
int number() const;
const odb_String description() const;
```
