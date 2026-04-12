# 62.1 SectionAssignment 对象

SectionAssignment 对象用于指定装配、部件或部件实例上的截面分配。装配上的截面分配仅限于连接器单元。

**访问**

```
odb.parts()[*name*].sectionAssignments(*i*)
odb.rootAssembly().instances()[*name*].sectionAssignments(*i*)
odb.rootAssembly().sectionAssignments(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.sectionAssignments(*i*)
```

### 62.1.1 成员

SectionAssignment 对象具有与 [SectionAssignment](pt02ch61pyo13.md#ker-odbassembly-sectionassignment-cpp) 方法参数相同名称和描述的成员。

此外，SectionAssignment 对象具有以下成员：

**原型**

```
 odb_Set region() const;
            odb_String sectionName() const;
            double offset() const;
```

*suppressed*

一个 Boolean，指定是否抑制截面分配。默认值为 false。
