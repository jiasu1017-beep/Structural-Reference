# 6.5 ModelInstance object







A ModelInstance object is an instance of a Model.

**Access**

```
import assembly
mdb.models[*name*].rootAssembly.modelInstances[*i*]
```

### 6.5.1 Instance(...)

This method creates a ModelInstance object and puts it into the instances repository.

**Path**

```
mdb.models[*name*].rootAssembly.Instance
```

**Required arguments**

*name*

The repository key. The name must be a valid Abaqus object name.

*model*

A [Model](pt01ch33pyo01.md) object to be instanced. If the model does not exist, no ModelInstance object is created.

**Optional argument**

*autoOffset*

A Boolean specifying whether to apply an auto offset to the new instance that will offset it from existing instances. The default value is OFF.

**Return value**

A ModelInstance object.

**Exceptions**

None.

### 6.5.2 ConvertConstraints()

This method converts the position constraints of an instance to absolute positions. The method deletes the constraint features on the instance but preserves the position in space.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.5.3 getPosition()

This method prints the sum of the translations and rotations applied to the ModelInstance object.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.5.4 translate(...)

This method translates an instance by the specified amount.

**Required argument**

*vector*

A sequence of three Floats specifying a translation vector.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.5.5 Members

The ModelInstance object can have the following members:

*sets*

A repository of [Set](pt01ch45pyo04.md) objects specifying the sets created on the assembly. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*surfaces*

A repository of [Surface](pt01ch45pyo05.md) objects specifying the surfaces created on the assembly. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*vertices*

A [VertexArray](pt01ch07pyo15.md) object.

*edges*

An [EdgeArray](pt01ch07pyo03.md) object.

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object.

*nodes*

A [MeshNodeArray](pt01ch31pyo09.md) object.

*datums*

A repository of [Datum](pt01ch15pyo01.md) objects.

*referencePoints*

A repository of [ReferencePoint](pt01ch07pyo13.md) objects.




