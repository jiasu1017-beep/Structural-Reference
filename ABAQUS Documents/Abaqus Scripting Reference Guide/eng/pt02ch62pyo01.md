# 62.1 SectionAssignment object







The SectionAssignment object is used to specify a section assignment on an assembly, part or part instance. Section assignments on the assembly are limited to connector elements only.

**Access**

```
odb.parts()[*name*].sectionAssignments(*i*)
odb.rootAssembly().instances()[*name*].sectionAssignments(*i*)
odb.rootAssembly().sectionAssignments(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.sectionAssignments(*i*)
```

### 62.1.1 Members

The SectionAssignment object has members with the same names and descriptions as the arguments to the [SectionAssignment](pt02ch61pyo13.md#ker-odbassembly-sectionassignment-cpp) method.

In addition, the SectionAssignment object has the following member:

**Prototype**

```
 odb_Set region() const;
            odb_String sectionName() const;
            double offset() const;

```

*suppressed*

A Boolean specifying whether the section assignment is suppressed or not. The default value is false.




