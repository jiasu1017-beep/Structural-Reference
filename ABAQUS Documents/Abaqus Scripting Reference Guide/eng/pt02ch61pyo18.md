# 61.18 OdbMeshElement object







 OdbMeshElement               objects are created with the `part.addElements`               or `rootAssembly.addElements`               methods.

**Access**

```
odb.parts()[*name*].elements(*i*)
odb.parts()[*name*].elementSets()[*name*].elements(*i*)
odb.parts()[*name*].nodeSets()[*name*].elements(*i*)
odb.parts()[*name*].surfaces()[*name*].elements(*i*)
odb.rootAssembly().elements(*i*)
odb.rootAssembly().elementSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)
odb.rootAssembly().nodeSets()[*name*].elements(*i*)
odb.rootAssembly().surfaces()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*)
```

### 61.18.1 Members

The OdbMeshElement object can have the following members:

**Prototype**

```
int label() const;
               const int* connectivity(int& numNodes) const ;
               odb_SequenceInt connectivity() const;
               odb_SectionCategory sectionCategory() const;
               odb_String type() const;
               odb_String instanceName() const;
               odb_SequenceString instanceNames() const;
```

*label*

An Int specifying the element label.

*type*

An odb_String specifying the element type.

*sectionCategory*

A [SectionCategory](pt02ch61pyo27.md) object specifying the element section properties.

*connectivity*

A pointer to an array of Ints specifying the element connectivity. For connector elements connected to ground, the other node is repeated in the connectivity data. The position of the ground node cannot be ascertained. This is a limitation. It is important to note the difference with MeshElement object of MDB where the connectivity is node indices instead of node labels.

*instanceNames*

A pointer to an array of Strings specifying the instance names for nodes in the element connectivity.

*instanceName*

An odb_String specifying the instance name.




