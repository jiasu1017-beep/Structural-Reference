# 6.4 PartInstance object







A PartInstance object is an instance of a Part object.

**Access**

```
import assembly
mdb.models[*name*].rootAssembly.allinstances
mdb.models[*name*].rootAssembly.instances[*name*]
```

### 6.4.1 Instance(...)

This method creates a PartInstance object and puts it into the instances repository.

**Path**

```
mdb.models[*name*].rootAssembly.Instance
```

**Required arguments**

*name*

A String specifying the repository key. The name must be a valid Abaqus object name.

*part*

A [Part](pt01ch37pyo01.md) object to be instanced. If the part does not exist, no PartInstance object is created.

**Optional arguments**

*autoOffset*

A Boolean specifying whether to apply an auto offset to the new part instance that will offset it from existing part instances. The default value is OFF.

*dependent*

A Boolean specifying whether the part instance is dependent or independent. If *dependent*=OFF, the part instance is independent. The default value is OFF.

**Return value**

A PartInstance object.

**Exceptions**

None.

### 6.4.2 InstanceFromBooleanCut(...)

This method creates a PartInstance in the `instances` repository after subtracting or cutting the geometries of a group of part instances from that of a base part instance.

**Path**

```
mdb.models[*name*].rootAssembly.InstanceFromBooleanCut
```

**Required arguments**

*name*

A String specifying the repository key. The name must be a valid Abaqus object name.

*instanceToBeCut*

A PartInstance specifying the base instance from which to cut other instances.

*cuttingInstances*

A sequence of PartInstance objects specifying the instances with which to cut the base instance.

**Optional argument**

*originalInstances*

A SymbolicConstant specifying whether the original instances should be suppressed or deleted after the merge operation. Possible values are SUPPRESS or DELETE. The default value is SUPPRESS.

**Return value**

A PartInstance object.

**Exceptions**

None.

### 6.4.3 InstanceFromBooleanMerge(...)

This method creates a PartInstance in the `instances` repository after merging two or more part instances.

**Path**

```
mdb.models[*name*].rootAssembly.InstanceFromBooleanMerge
```

**Required arguments**

*name*

A String specifying the repository key. The name must be a valid Abaqus object name.

*instances*

A sequence of PartInstance objects specifying the part instances to merge.

**Optional arguments**

*keepIntersections*

A Boolean specifying whether the boundary intersections of Abaqus native part instances should be retained after the merge operation. The default value is False.

*originalInstances*

A SymbolicConstant specifying whether the original instances should be suppressed or deleted after the merge operation. Possible values are SUPPRESS or DELETE. The default value is SUPPRESS.

*domain*

A SymbolicConstant specifying whether geometry or mesh of the specified part instances is to be merged. Possible values are GEOMETRY, MESH or BOTH. The default value is GEOMETRY.

*mergeNodes*

A SymbolicConstant specifying which nodes of the specified part instances should be considered for merging. This argument is only applicable if *domain* is MESH. Possible values are BOUNDARY_ONLY, ALL, or NONE. The default value is BOUNDARY_ONLY.

*nodeMergingTolerance*

A Float specifying the maximum distance between nodes of the specified part instances that will be merged and replaced with a single node in the new part. The location of the new node is the average position of the deleted nodes. This argument is only applicable if *domain* is MESH. The default value is 10–6.

*removeDuplicateElements*

A Boolean specifying whether elements with the same connectivity in the new part will be merged into a single element. This argument is only applicable if *domain* is MESH. The default value is True.

**Return value**

A PartInstance object.

**Exceptions**

None.

### 6.4.4 LinearInstancePattern(...)

This method creates multiple PartInstance objects in a linear pattern and puts them into the instances repository.

**Path**

```
mdb.models[*name*].rootAssembly.LinearInstancePattern
```

**Required arguments**

*instanceList*

A sequence of Strings specifying the names of instances to pattern.

*number1*

An Int specifying the total number of instances, including the original instances, that appear along the first direction in the pattern.

*spacing1*

A Float specifying the spacing between instances along the first direction in the pattern.

*number2*

An Int specifying the total number of instances, including the original instances, that appear along the second direction in the pattern.

*spacing2*

A Float specifying the spacing between instances along the second direction in the pattern.

**Optional arguments**

*direction1*

A sequence of three Floats specifying a vector along the first direction. The default value is (1.0, 0.0, 0.0).

*direction2*

A sequence of three Floats specifying a vector along the second direction. The default value is (0.0, 1.0, 0.0).

**Return value**

A sequence of PartInstance objects.

**Exceptions**

None.

### 6.4.5 RadialInstancePattern(...)

This method creates multiple PartInstance objects in a radial pattern and puts them into the instances repository.

**Path**

```
mdb.models[*name*].rootAssembly.RadialInstancePattern
```

**Required arguments**

*instanceList*

A sequence of Strings specifying the names of instances to pattern.

*number*

An Int specifying the total number of instances, including the original instances, that appear in the radial pattern. 

*totalAngle*

A Float specifying the total angle in degrees between the first and last instance in the pattern. A positive angle corresponds to a counter-clockwise direction. The values 360 and 360 represent a special case where the pattern makes a full circle. In this case, because the copy would overlay the original, the copy is not placed at the last position. Possible values are 360.0 ![](../graphics/ker_eqn00013.gif) *totalAngle* ![](../graphics/ker_eqn00013.gif) 360.0. 

**Optional arguments**

*point*

A sequence of three Floats specifying the center of the radial pattern. The default value is (0.0, 0.0, 0.0).

*axis*

A sequence of three Floats specifying the central axis of the radial pattern. The default value is (0.0, 0.0, 1.0).

**Return value**

A sequence of PartInstance objects.

**Exceptions**

None.

### 6.4.6 checkGeometry(...)

This method checks the validity of the geometry of the part instance and prints a count of all topological entities on the part instance (faces, edges, vertices, etc.).

**Required arguments**

None.

**Optional arguments**

*detailed*

A Boolean specifying whether detailed output will be printed to the replay file. The default value is OFF.

*level*

An Int specifying which level of checking is performed. Values can range from 20 to 70, with higher values reporting less and less important errors. The default value is 20, which reports all critical errors. When the default value is used, the stored validity status is updated to agree with the result of this check.

**Return value**

None

**Exceptions**

An exception is thrown if this is a dependent part instance and *level* was either not specified or was set to 20, because the validity status cannot be updated for a dependent part instance. In this case, this command should be called on the [Part](pt01ch37pyo01.md) instead.

```
The geometry of dependent part instances cannot be changed.
```

None.

### 6.4.7 Contact(...)

This method translates an instance along the specified direction until it is in contact with a fixed instance.

**Required arguments**

*movableList*

A sequence of [Face](pt01ch07pyo05.md) or [Edge](pt01ch07pyo03.md) objects on the part instance to be moved.

*fixedList*

A sequence of [Face](pt01ch07pyo05.md) or [Edge](pt01ch07pyo03.md) objects on the part instance to remain fixed.

*direction*

A sequence of three Floats specifying the direction of contact.

*clearance*

A Float specifying the distance between the two faces along the direction of contact.

**Optional argument**

*isFaceEdges*

A Boolean specifying how Abaqus calculates the contact. If *isFaceEdges* is OFF, contact is computed from the movable face to the fixed face. If *isFaceEdges* is ON, contact is computed using only the edges of the movable face and not its interior. The default value is OFF.

**Return value**

A [Feature](pt01ch20pyo01.md) object.

**Exceptions**

None.

### 6.4.8 ConvertConstraints()

This method converts the position constraints of an instance to absolute positions. The method deletes the constraint features on the instance but preserves the position in space.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.4.9 getPosition()

This method prints the sum of the translations and rotations applied to the PartInstance object.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.4.10 getRotation()

This method returns a tuple including the point of rotation, axis of rotation, and rotation angle (in degrees).

**Arguments**

None.

**Return value**

A tuple including the point of rotation, axis of rotation, and rotation angle (in degrees).

**Exceptions**

None.

### 6.4.11 getTranslation()

This method returns a tuple of three Floats representing translation in the *X*-, *Y*-, and *Z*-directions.

**Arguments**

None.

**Return value**

A tuple of three Floats representing the translation. 

**Exceptions**

None.

### 6.4.12 replace(...)

This method replaces one instance with an instance of another part.

**Required argument**

*instanceOf*

A [Part](pt01ch37pyo01.md) object specifying which Part will be instanced in place of the original [Part](pt01ch37pyo01.md).

**Optional argument**

*applyConstraints*

A Boolean specifying whether to apply existing constraints on the new instance or to position the new instance in the same place as the original instance. The default value is True. A value of False indicates that constraints applies to the instance are deleted will be deleted from the feature list.

**Return value**

None

**Exceptions**

None.

### 6.4.13 rotateAboutAxis(...)

This method translates an instance by the specified amount.

**Required arguments**

*axisPoint*

A sequence of three Floats specifying the *X*-, *Y*-, and *Z*-coordinates of a point on the axis.

*axisDirection*

A sequence of three Floats specifying the direction vector of the axis.

*angle*

A Float specifying the rotation angle in degrees. Use the right-hand rule to determine the direction.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.4.14 translate(...)

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

### 6.4.15 translateTo(...)

This method translates an instance along the specified direction until it is in contact with a fixed instance.

**Required arguments**

*movableList*

A sequence of [Face](pt01ch07pyo05.md) or [Edge](pt01ch07pyo03.md) objects on the part instance to be moved.

*fixedList*

A sequence of [Face](pt01ch07pyo05.md) or [Edge](pt01ch07pyo03.md) objects on the part instances to remain fixed.

*direction*

A sequence of three Floats specifying the direction of contact.

*clearance*

A Float specifying the distance between the two faces along the direction of contact.

**Optional argument**

*vector*

A sequence of three Floats specifying a translation vector. If this argument is specified, the movable instance will be translated by the specified amount without solving for the actual contact.

**Return value**

A [Feature](pt01ch20pyo01.md) object.

**Exceptions**

None.

### 6.4.16 Members

The PartInstance object can have the following members:

*name*

A String specifying the repository key. The name must be a valid Abaqus object name.

*dependent*

A Boolean specifying whether the part instance is dependent or independent. If *dependent*=OFF, the part instance is independent. The default value is OFF.

*excludedFromSimulation*

A Boolean specifying whether the part instance is excluded from the simulation. If *excludedFromSimulation*=ON, the part instance is excluded from the simulation. The default value is OFF.

*geometryValidity*

A Boolean specifying the validity of the geometry of the instance. The value is computed, but it can be set to ON to perform feature and mesh operations on an invalid instance. There is no guarantee that such operations will work if the instance was originally invalid.

*analysisType*

A SymbolicConstant specifying the part type. Possible values are DEFORMABLE_BODY, EULERIAN, DISCRETE_RIGID_SURFACE, and ANALYTIC_RIGID_SURFACE.

*referenceNode*

An Int specifying the reference node number. This member is valid only if *analysisType*=DISCRETE_RIGID_SURFACE or ANALYTIC_RIGID_SURFACE.

*part*

A [Part](pt01ch37pyo01.md) object specifying the instanced part.

*sets*

A repository of [Set](pt01ch45pyo04.md) objects specifying the sets created on the part. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*surfaces*

A repository of [Surface](pt01ch45pyo05.md) objects specifying the surfaces created on the part. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*skins*

A repository of [Skin](pt01ch45pyo06.md) objects specifying the skins created on the part. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*stringers*

A repository of [Stringer](pt01ch45pyo07.md) objects specifying the stringers created on the part. For more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*vertices*

A [VertexArray](pt01ch07pyo15.md) object.

*ignoredVertices*

An [IgnoredVertexArray](pt01ch07pyo09.md) object.

*edges*

An [EdgeArray](pt01ch07pyo03.md) object.

*ignoredEdges*

An [IgnoredEdgeArray](pt01ch07pyo07.md) object.

*faces*

A [FaceArray](pt01ch07pyo05.md) object.

*cells*

A [CellArray](pt01ch07pyo01.md) object.

*datums*

A repository of [Datum](pt01ch15pyo01.md) objects.

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object.

*nodes*

A [MeshNodeArray](pt01ch31pyo09.md) object.

*elemFaces*

A repository of [MeshFace](pt01ch31pyo08.md) objects specifying all the element faces in the part instance. For a given element and a given face index within that element, the corresponding [MeshFace](pt01ch31pyo08.md) object can be retrieved from the repository by using the key calculated as (i*8 + j), where i and j are zero-based element and face indices, respectively.

*elementFaces*

A [MeshFaceArray](pt01ch31pyo08.md) object.

*elemEdges*

A repository of [MeshEdge](pt01ch31pyo04.md) objects specifying all the element edges in the part instance. For a given element and a given edge index on a given face within that element, the corresponding [MeshEdge](pt01ch31pyo04.md) object can be retrieved from the repository by using the key calculated as (i*32 + j*4 + k), where i, j, and k are zero-based element, face, and edge indices, respectively.

*elementEdges*

A [MeshEdgeArray](pt01ch31pyo04.md) object.

*referencePoints*

A repository of [ReferencePoint](pt01ch07pyo13.md) objects.

*partName*

A String specifying the name of the part from which the instance was created.




