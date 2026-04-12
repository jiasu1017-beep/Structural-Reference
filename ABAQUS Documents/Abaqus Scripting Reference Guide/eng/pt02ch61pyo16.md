# 61.16 OdbInstance object







A part instance is the usage of a part within an assembly.

**Access**

```
odb.rootAssembly().instances()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()
```

### 61.16.1 Instance(...)

This method creates an OdbInstance                     object from an [OdbPart](pt02ch61pyo20.md)                     object.

**Path**

```
odb.rootAssembly().Instance
```

**Prototype**

```
odb_Instance&
Instance(const odb_String& name,
         const odb_Part& object,
         const odb_SequenceSequenceFloat& localCoordSystem);
```

**Required arguments**

*name*

An odb_String specifying the instance name.

*object*

An [OdbPart](pt02ch61pyo20.md)                              object.

**Optional argument**

*localCoordSystem*

An odb_SequenceSequenceFloat specifying the rotation and translation of the part instance in the global Cartesian coordinate system. The first three sequences specify the new local coordinate system with its center at the origin.
- The first sequence specifies a point on the 1-axis.
- The second sequence specifies a point on the 2-axis.
- The third sequence specifies a point on the 3-axis.

                              The fourth sequence specifies the translation of the local coordinate system from the origin to its intended location.

For example, the following sequence moves a part 10 units in the *X*-direction with no rotation:

```
localCoordSystem = ((1, 0, 0), (0, 1, 0),
                                 (0, 0, 1), (10, 0, 0))
```

The following sequence moves a part 5 units in the *X*-direction with rotation:

```
localCoordSystem = ((0, 1, 0), (1, 0, 0),
                                 (0, 0, 1), (5, 0, 0))
```
                                 transforms a part containing the two points 
```

                                 Pt1= (1,0,0) 
                                 Pt2= (2,0,0) 

```
                                to
```

                                 Pt1 = (0, 6, 0) 
                                 Pt2 = (0, 7, 0)                      

```

**Return value**

An OdbInstance                     object.

**Exceptions**

InvalidNameError.

### 61.16.2 assignBeamOrientation(...)

This method assigns a beam section orientation to a region of a part instance.

**Prototype**

```
void
assignBeamOrientation(const odb_Set& region,
                  odb_Enum::odb_OrientationMethodEnum method,
                  const odb_SequenceFloat& vector);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region on an instance.

*method*

An odb_Enum::odb_OrientationMethodEnum specifying the assignment method. Only a value of odb_Enum::N1_COSINES                              is currently supported.

*vector*

An odb_SequenceFloat specifying the approximate local ![](../graphics/ker_eqn00406.gif)-direction of the beam cross-section.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.16.3 assignMaterialOrientation(...)

This method assigns a material orientation to a region of a part instance.

**Prototype**

```
void
assignMaterialOrientation(const odb_Set& region,
             const odb_DatumCsys& localCsys,
             odb_Enum::odb_AxisEnum axis,
             float angle,
             odb_Enum::odb_StackDirectionEnum stackDirection);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region on an instance.

*localCsys*

An [OdbDatumCsys](pt02ch61pyo14.md)                              object specifying the local coordinate system or `None`, indicating the global coordinate system.

**Optional arguments**

*axis*

An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3. The default value is odb_Enum::AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

*stackDirection*

An odb_Enum::odb_StackDirectionEnum specifying the stack or thickness direction of the material. Possible values are odb_Enum::STACK_1, odb_Enum::STACK_2, odb_Enum::STACK_3, and odb_Enum::STACK_ORIENTATION. The default value is odb_Enum::STACK_3.

**Return value**

None

**Exceptions**

None.

### 61.16.4 assignRebarOrientation(...)

This method assigns a rebar reference orientation to a region of a part instance.

**Prototype**

```
void
assignRebarOrientation(const odb_Set& region,
                       const odb_DatumCsys& localCsys,
                       odb_Enum::odb_AxisEnum axis,
                       float angle);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region on an instance.

*localCsys*

An [OdbDatumCsys](pt02ch61pyo14.md)                              object specifying the local coordinate system or `None`, indicating the global coordinate system.

**Optional arguments**

*axis*

An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3. The default value is odb_Enum::AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

**Return value**

None

**Exceptions**

None.

### 61.16.5 getElementFromLabel(...)

This method is used to retrieved an element with a specific label from an instance object.

**Prototype**

```
odb_Element
getElementFromLabel(int label);
```

**Required argument**

*label*

An Int specifying the element label.

**Optional arguments**

None.

**Return value**

An [OdbMeshElement](pt02ch61pyo18.md)                     object.

**Exceptions**

If no element with the specified label exists:

```
OdbError: Invalid element label
```

### 61.16.6 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

**Prototype**

```
odb_Node
getNodeFromLabel(int label);
```

**Required argument**

*label*

An Int specifying the node label.

**Optional arguments**

None.

**Return value**

An[OdbMeshNode](pt02ch61pyo19.md)                     object.

**Exceptions**

If no node with the specified label exists:

```
OdbError: Invalid node label
```

### 61.16.7 assignSection(...)

This method is used to assign a section to a region on an instance.

**Prototype**

```
void
assignSection(const odb_Set& region,
              const odb_section& section);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region on an instance.

*section*

A [Section](pt02ch63pyo01.md)                              object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If *region*                           is not an element set:

```
OdbError: Section assignment requires element set.
```

If the element set is not from the current instance:

```
OdbError: Section assignment requires element set from this part instance.
```

### 61.16.8 AnalyticRigidSurf2DPlanar(...)

This method is used to define a two-dimensional [AnalyticSurface](pt02ch61pyo02.md)                     object on the instance.

**Prototype**

```
void
AnalyticRigidSurf2DPlanar(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius);
```

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt02ch61pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md)                              object.

**Optional argument**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

**Return value**

None

**Exceptions**

If [OdbPart](pt02ch61pyo20.md)                           associated with the part instance is of type THREE_D:

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the instance is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 61.16.9 AnalyticRigidSurfExtrude(...)

This method is used to define a three-dimensional cylindrical [AnalyticSurface](pt02ch61pyo02.md)                     on the instance.

**Prototype**

```
void
AnalyticRigidSurfExtrude(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius,
           const odb_SequenceSequenceFloat& localCoordData);
```

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt02ch61pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md)                              object.

**Optional arguments**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

*localCoordData*

An odb_SequenceSequenceFloat specifying the global coordinates of points used to define the local coordinate system.

**Return value**

None

**Exceptions**

If [OdbPart](pt02ch61pyo20.md)                           associated with the part instance is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                             CYLINDER                            can be defined only if the instance is of type                             THREE_D.                         
```

### 61.16.10 AnalyticRigidSurfRevolve(...)

This method is used to define a three-dimensional [AnalyticSurface](pt02ch61pyo02.md)                     of revolution on the instance.

**Prototype**

```
void
AnalyticRigidSurfRevolve(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius,
           const odb_SequenceSequenceFloat& localCoordData);
```

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt02ch61pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md)                              object.

**Optional arguments**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

*localCoordData*

An odb_SequenceSequenceFloat specifying the global coordinates of points used to define the local coordinate system.

**Return value**

None

**Exceptions**

If [OdbPart](pt02ch61pyo20.md)                           associated with the part instance is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the instance is of type                             THREE_D.                         
```

### 61.16.11 RigidBody(...)

This method defines an [OdbRigidBody](pt02ch61pyo22.md)                     on the instance.

**Prototype**

```
void
RigidBody(const odb_Set& referenceNode,
          odb_Enum::odb_PositionEnum position,
          bool isothermal,
          const odb_Set& elset,
          const odb_Set& pinNodes,
          const odb_Set& tieNodes);
```

**Required argument**

*referenceNode*

An [OdbSet](pt02ch61pyo24.md)                              specifying the reference node assigned to the rigid body.

**Optional arguments**

*position*

A symbolic constant specify if the location of the reference node is to be defined by the user. Possible values are odb_Enum::INPUT, and odb_Enum::CENTER_OF_MASS. The default value is odb_Enum::INPUT.

*isothermal*

A Boolean specifying an isothermal rigid body.  The default value is false. This parameter is used only for a fully-coupled thermal stress analysis.

*elset*

An [OdbSet](pt02ch61pyo24.md)                              specifying an element set assigned to the rigid body.

*pinNodes*

An [OdbSet](pt02ch61pyo24.md)                              specifying pin-type nodes assigned to the rigid body.

*tieNodes*

An [OdbSet](pt02ch61pyo24.md)                              specifying tie-type nodes assigned to the rigid body.

**Return value**

None

**Exceptions**

If *referenceNode*                           is not a node set:

```
OdbError: Rigid body definition requires a node set.
```

### 61.16.12 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

**Prototype**

```
odb_Node
getNodeFromLabel(int label);
```

**Required argument**

*label*

An Int specifying the node label.

**Optional arguments**

None.

**Return value**

An [OdbMeshNode](pt02ch61pyo19.md)                     object.

**Exceptions**

If no node with the specified label exists:

```
OdbError: Invalid node label
```

### 61.16.13 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

**Prototype**

```
odb_Node
getNodeFromLabel(int label);
```

**Required argument**

*label*

An Int specifying the node label.

**Optional arguments**

None.

**Return value**

An [OdbMeshNode](pt02ch61pyo19.md)                     object.

**Exceptions**

If no node with the specified label exists:

```
OdbError: Invalid node label
```

### 61.16.14 nodesLabelsFromNodeTypeFace(...)

Given a sequence of integers defining an element connectivity, this method is used to retrieve the sequence of nodes attached to a specified face of the element based on element type.

**Prototype**

```
odb_SequenceInt
nodesLabelsFromNodeTypeFace(const odb_SequenceInt& elementNodeLabels,
               const odb_String& elementType,
               odb_Enum::odb_ElementFaceEnumEnum elementFace);
```

**Required arguments**

*elementNodeLabels*

A sequence of Ints specifying the node labels defining the connectivity for the entire element.

*elementType*

A string specifying the type of element whose connectivity is provided.

*elementFace*

A SymbolicConstant specifying the face of the element for which the node labels are desired.

**Optional arguments**

None.

**Return value**

A sequence of Ints specifying the node labels corresponding to the desired element face.

**Exceptions**

If the specified face is invalid for the element type:

```
OdbError: Invalid face
```

### 61.16.15 Members

The OdbInstance object can have the following members:

**Prototype**

```
odb_String name() const;
               odb_Enum::odb_DimensionEnum embeddedSpace() const;
               odb_Enum::odb_PartTypeEnum type() const;
               odb_Node nodes(int i) const;
               odb_SequenceNode& nodes() const;
               odb_Element elements(int i) const;
               odb_SequenceElement& elements() const;
               odb_SetRepository& nodeSets() const;
               odb_SetRepository& elementSets() const;
               odb_SetRepository& surfaces() const;
               odb_SequenceSectionAssignment sectionAssignments()\
                   const;
               odb_SequenceBeamOrientation beamOrientations() \
                   const;
               odb_SequenceMaterialOrientation materialOrientations() \
                   const;
               odb_SequenceRebarOrientation rebarOrientations() \
                   const;
               odb_SequenceRigidBody rigidBodies() const;
               bool hasAnalyticSurface() const;
               odb_AnalyticSurface analyticSurface() const;
```

*name*

An odb_String specifying the instance name.

*type*

An odb_Enum::odb_PartTypeEnum specifying the type of the [OdbPart](pt02ch61pyo20.md)                  object. Only a value of odb_Enum::DEFORMABLE_BODY                  is currently supported.

*embeddedSpace*

An odb_Enum::odb_DimensionEnum specifying the dimensionality of the [OdbPart](pt02ch61pyo20.md)                  object.                 Possible values are odb_Enum::THREE_D, odb_Enum::TWO_D_PLANAR, odb_Enum::AXISYMMETRIC, and odb_Enum::UNKNOWN_DIMENSION.

*resultState*

An odb_Enum::odb_ResultStateEnum specifying the state of the Instance as modified by the analysis. This member is only present if the Instance is part of the RootAssemblyState tree. Possible values are:
- odb_Enum::PROPAGATED, specifying that the value is the same as the previous frame or the original rootAssembly.
- odb_Enum::MODIFIED, specifying that the geometry of the instance has been changed at this frame.

The default value is odb_Enum::PROPAGATED.

*nodes*

A sequence of [OdbMeshNode](pt02ch61pyo19.md) objects.

*elements*

A sequence of [OdbMeshElement](pt02ch61pyo18.md) objects.

*nodeSets*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying node sets.

*elementSets*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying element sets.

*surfaces*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying surfaces.

*sectionAssignments*

A sequence of [SectionAssignment](pt02ch62pyo01.md) objects.

*rigidBodies*

A sequence of [OdbRigidBody](pt02ch61pyo22.md) objects.

*beamOrientations*

A sequence of [BeamOrientation](pt02ch61pyo04.md) objects.

*materialOrientations*

A sequence of [MaterialOrientation](#ker-materialorientation-cpp) objects.

*rebarOrientations*

A sequence of [RebarOrientation](pt02ch61pyo26.md) objects.

*analyticSurface*

An [AnalyticSurface](pt02ch61pyo02.md) object specifying analytic Surface defined on the instance.




