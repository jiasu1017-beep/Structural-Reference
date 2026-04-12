# 61.24 OdbSet object







The set objects are used to identify regions of a model.

**Access**

```
odb.parts()[*name*].elementSets()[*name*]
odb.parts()[*name*].nodeSets()[*name*]
odb.parts()[*name*].surfaces()[*name*]
odb.rootAssembly().elementSets()[*name*]
odb.rootAssembly().instances()[*name*].elementSets()[*name*]
odb.rootAssembly().instances()[*name*].nodeSets()[*name*]
odb.rootAssembly().instances()[*name*].surfaces()[*name*]
odb.rootAssembly().nodeSets()[*name*]
odb.rootAssembly().surfaces()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*]
```

### 61.24.1 NodeSet(...)

This method creates a node set from an array of [OdbMeshNode](pt02ch61pyo19.md)                     objects (for part instance-level sets)

**Path**

```
odb.parts()[*name*].NodeSet
```

```
odb.rootAssembly().instances()[*name*].NodeSet
```

**Prototype**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceNode& nodes);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*nodes*

A sequence of [OdbMeshNode](pt02ch61pyo19.md)                              objects. For example, for a part:

```
nodes=part1.nodes[1:5]
```

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

InvalidNameError.

### 61.24.2 ElementSet(...)

This method creates an element set from an array of [OdbMeshElement](pt02ch61pyo18.md)                     objects (for part instance-level sets).

**Path**

```
odb.parts()[*name*].ElementSet
```

```
odb.rootAssembly().instances()[*name*].ElementSet
```

**Prototype**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceElement& elements);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*elements*

A sequence of [OdbMeshElement](pt02ch61pyo18.md)                              objects. For example, for a part:

```
elements=instance1.elements[1:5]
```

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

InvalidNameError.

### 61.24.3 NodeSet(...)

This method creates a node set.

**Path**

```
odb.parts()[*name*].NodeSet                   
```

```
odb.rootAssembly().instances()[*name*].NodeSet                   
```

**Prototype**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceInt& nodeLabels);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*nodeLabels*

An odb_SequenceInt specifying the node labels.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.4 NodeSet(...)

This method creates a node set.

**Path**

```
odb.rootAssembly().NodeSet
```

**Prototype**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceString& instanceNames,
        const odb_SequenceSequenceInt& nodeLabels);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*instanceNames*

An odb_SequenceString specifying the namespaces for *nodeLabels*. The string could be an empty string to denote the nodeLabels at the assembly level.

*nodeLabels*

An odb_SequenceSequenceInt specifying the node labels.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.5 ElementSet(...)

This method creates an element set.

**Path**

```
odb.parts()[*name*].ElementSet                   
```

```
odb.rootAssembly().instances()[*name*].ElementSet                   
```

**Prototype**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceInt& elementLabels);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*elementLabels*

An odb_SequenceInt specifying the element labels.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.6 ElementSet(...)

This method creates an element set.

**Path**

```
odb.rootAssembly().ElementSet
```

**Prototype**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceString& instanceNames,
           const odb_SequenceSequenceInt& elementLabels);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*instanceNames*

An odb_SequenceString specifying the namespaces for *elementLabels*. The string could be an empty string to denote the elementLabels at the assembly level.                   

*elementLabels*

An odb_SequenceSequenceInt specifying the element labels.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.7 Surface(...)

This method creates a surface set.

**Path**

```
odb.parts()[*name*].Surface                   
```

```
odb.rootAssembly().instances()[*name*].Surface                   
```

**Prototype**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceElement& elements,
        const odb_SequenceElementFace& faces);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*elements*

An odb_SequenceElement specifying the elements in the surface.

*faces*

An odb_SequenceElementFace                              specifying the element faces.

The possible face enumerations depend on the type of element, as described in the following table:

| Element type | Face enumerations |
| --- | --- |
| Solid elements | FACE1, FACE2, FACE3, FACE4, FACE5, FACE6 |
| Three-dimensional shell elements | SIDE1, SIDE2 |
| Two-dimensional elements | FACE1, FACE2, FACE3, FACE4 |
| Wire elements | END, END2 |

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.8 Surface(...)

This method creates a surface set.

**Path**

```
odb.parts()[*name*].Surface                   
```

```
odb.rootAssembly().instances()[*name*].Surface                   
```

**Prototype**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceInt& elementLabels,
        const odb_SequenceElementFace& faces);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*elementLabels*

An odb_SequenceInt specifying the element labels.

*faces*

An odb_SequenceElementFace                              specifying the element faces. An odb_SequenceSequenceElementFace                              is required for an assembly set.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.9 Surface(...)

This method creates a surface set.

**Path**

```
odb.rootAssembly().Surface
```

**Prototype**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceString& instanceNames,
        const odb_SequenceSequenceInt& elementLabels,
        const odb_SequenceSequenceElementFace& faces);
```

**Required arguments**

*name*

An odb_String specifying the name of the set and the repository key.

*instanceNames*

An odb_SequenceString specifying the namespaces for *elementLabels*. This member is only valid for assembly sets. The string could be an empty string to denote the elementLabels at the assembly level.                   

*elementLabels*

An odb_SequenceSequenceInt specifying the element labels.

*faces*

An odb_SequenceSequenceElementFace specifying the element faces.

**Optional arguments**

None.

**Return value**

An OdbSet                     object.

**Exceptions**

None.

### 61.24.10 Members

The OdbSet object can have the following members:

**Prototype**

```
odb_String name() const;
               odb_SequenceString instanceNames();
               odb_Node nodes(int index);
               const odb_SequenceNode& nodes();
               const odb_SequenceNode& nodes(const odb_String& \
                   instanceName); // For an assembly level set
               odb_Element elements(int index);
               const odb_SequenceElement& elements();
               const odb_SequenceElement& elements(const odb_String& \
                   instanceName); // For an assembly level set
               odb_Enum::odb_ElementFaceEnum faces(int index);
               const odb_SequenceElementFace& faces() ;
               const odb_SequenceElementFace& faces(const odb_String& \
                    instanceName); // For an assembly level set
               odb_Enum::odb_SetTypeEnum type() const;
```

*name*

An odb_String specifying the name of the set and the repository key.

*instanceNames*

An odb_SequenceString specifying the namespaces for the nodes, elements, and faces constituting the set.

*nodes*

A sequence of [OdbMeshNode](pt02ch61pyo19.md) objects.

*elements*

A sequence of [OdbMeshElement](pt02ch61pyo18.md) objects.

*faces*

An odb_SequenceElementFace specifying the element face.




