# 45.5 Surface object







The Surface object stores surfaces selected from the assembly. A surface is comprised of geometric or discrete entities but not both. An instance of a Surface object is available from the *surface* member of the Assembly object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*]
mdb.models[*name*].parts[*name*].surfaces[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]
mdb.models[*name*].rootAssembly.surfaces[*name*]
```

### 45.5.1 Surface(...)

 This method creates a surface from a sequence of objects in a model database. The surface will apply to the sides specified by the arguments.For example,

```
surface=mdb.models['Model-1'].parts['Part-1'].Surface(side1Faces=side1Faces, name='Surf-1')
```

**Path**

```
mdb.models[*name*].parts[*name*].Surface
```

```
mdb.models[*name*].rootAssembly.Surface
```

**Required argument**

 On three-dimensional solid faces, you can use the following arguments:
- *side1Faces*
- *side2Faces*

On three-dimensional shell faces, you can use the following arguments:- *side1Faces*
- *side2Faces*
- *side12Faces*

 On three-dimensional wire edges, you can use the following arguments: - *end1Edges*
- *end2Edges*
- *circumEdges*

On three-dimensional or two-dimensional or axisymmetric edges, you can use the following arguments:- *side1Edges*
- *side2Edges*

On two-dimensional or axisymmetric shell elements, you can use the following arguments:- *face1Elements*
- *face2Elements*
- *face3Elements*
- *face14Elements*

On solid elements, you can use the following arguments: - *face1Elements*
- *face2Elements*
- *face3Elements*
- *face4Elements*
- *face5Elements*
- *face6Elements*

On three-dimensional shell elements, you can use the following arguments:- *side1Elements*
- *side2Elements*
- *side12Elements*

On three-dimensional wire elements, you can use the following arguments:- *end1Elements*
- *end2Elements*
- *circumElements*

On two-dimensional or axisymmetric wire elements, you can use the following arguments:- *side1Elements*
- *side2Elements*

*name*

A String specifying the repository key. The default value is an empty string.

**Optional arguments**

*side1Elements*

A sequence of [MeshElement](pt01ch31pyo05.md) objects (surface applies to SIDE1 of element). The default value is `None`.

*side2Elements*

A sequence of [MeshElement](pt01ch31pyo05.md) objects (surface applies to SIDE2 of element). The default value is `None`.

*side12Elements*

A sequence of MeshElement objects (surface applies to both SIDE1 and SIDE2 of element). The default value is `None`.

*end1Elements*

A sequence of MeshElement objects (surface applies to END1 of element). The default value is `None`.

*end2Elements*

A sequence of MeshElement objects (surface applies to END2 of element). The default value is `None`.

*circumElements*

A sequence of MeshElement objects (surface applies to circumference of element). The default value is `None`.

*face1Elements*

A sequence of MeshElement objects (surface applies to FACE1 of element). The default value is `None`.

*face2Elements*

A sequence of MeshElement objects (surface applies to FACE2 of element). The default value is `None`.

*face3Elements*

A sequence of MeshElement objects (surface applies to FACE3 of element). The default value is `None`.

*face4Elements*

A sequence of MeshElement objects (surface applies to FACE4 of element). The default value is `None`.

*face5Elements*

A sequence of MeshElement objects (surface applies to FACE5 of element). The default value is `None`.

*face6Elements*

A sequence of MeshElement objects (surface applies to FACE6 of element). The default value is `None`.

*side1Faces*

A sequence of Face objects (surface applies to SIDE1 of face). The default value is `None`.

*side2Faces*

A sequence of Face objects (surface applies to SIDE2 of face). The default value is `None`.

*side12Faces*

A sequence of Face objects (surface applies to both SIDE1 and SIDE2 of face). The default value is `None`.

*side1Edges*

A sequence of Edge objects (surface applies to SIDE1 of edge). The default value is `None`.

*side2Edges*

A sequence of Edge objects (surface applies to SIDE2 of edge). The default value is `None`.

*end1Edges*

A sequence of Edge objects (surface applies to END1 of edge). The default value is `None`.

*end2Edges*

A sequence of Edge objects (surface applies to END2 of edge). The default value is `None`.

*circumEdges*

A sequence of Edge objects (surface applies circumferentially to edge). The default value is `None`.

**Return value**

A Surface object.

**Exceptions**

InvalidNameError.

### 45.5.2 SurfaceByBoolean(...)

This method creates a surface by performing a boolean operation on two or more input surfaces.

**Path**

```
mdb.models[*name*].parts[*name*].SurfaceByBoolean
```

```
mdb.models[*name*].rootAssembly.SurfaceByBoolean
```

**Required arguments**

*name*

A String specifying the repository key.

*surfaces*

A sequence of Surface objects.

**Optional argument**

*operation*

A SymbolicConstant specifying the boolean operation to perform. Possible values are UNION, INTERSECTION, andDIFFERENCE. The default value is UNION. Note that if DIFFERENCE is specified, the order of the given input surfaces is important; All surfaces specified after the first one are subtracted from the first one.

**Return value**

A Surface object.

**Exceptions**

InvalidNameError.

### 45.5.3 SurfaceFromElsets(...)

This method creates a surface from a sequence of element sets in a model database.

**Path**

```
mdb.models[*name*].rootAssembly.SurfaceFromElsets
```

**Required arguments**

*name*

A String specifying the repository key.

*elementSetSeq*

A sequence of element sets. For example, 

```
elementSetSeq=((elset1, S1),(elset2, S2))
```
where `elset1=mdb.models[*name*].rootAssembly.sets['Clutch']` and `S1` and `S2` indicate the side of the element set.

**Optional arguments**

None.

**Return value**

A Surface object.

**Exceptions**

InvalidNameError.

### 45.5.4 Members

The Surface object can have the following members:

*edges*

An [EdgeArray](pt01ch07pyo03.md) object.

*faces*

A [FaceArray](pt01ch07pyo05.md) object.

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object.

*nodes*

A [MeshNodeArray](pt01ch31pyo09.md) object.

*sides*

A tuple of SymbolicConstants specifying the sides; for example, (SIDE1, SIDE2).

*instances*

A tuple of Ints specifying the instances. This member is not applicable for a Surface object on an output database.




