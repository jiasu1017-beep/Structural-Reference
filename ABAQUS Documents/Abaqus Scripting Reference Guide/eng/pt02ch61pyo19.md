# 61.19 OdbMeshNode object







OdbMeshNode objects are created with the `part.addNodes` method.

**Access**

```
odb.parts()[*name*].elementSets()[*name*].nodes(*i*)
odb.parts()[*name*].nodes(*i*)
odb.parts()[*name*].nodeSets()[*name*].nodes(*i*)
odb.parts()[*name*].surfaces()[*name*].nodes(*i*)
odb.rootAssembly().elementSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].nodes(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].nodes(*i*)
odb.rootAssembly().nodes(*i*)
odb.rootAssembly().nodeSets()[*name*].nodes(*i*)
odb.rootAssembly().surfaces()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].nodes(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].nodes(*i*)
```

### 61.19.1 Members

The OdbMeshNode object has the following members:

**Prototype**

```
int label() const;
const float* coordinates() const;
```

*label*

An Int specifying the node label.

*coordinates*

A pointer to an array of Floats specifying the nodal coordinates in the global Cartesian coordinate system.




