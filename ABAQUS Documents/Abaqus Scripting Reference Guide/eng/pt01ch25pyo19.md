# 25.19 ContactExp object







The ContactExp object defines the contact domain and associated properties during contact in an Abaqus/Explicit analysis.

The ContactExp object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.19.1 ContactExp(...)

This method creates a ContactExp object.

**Path**

```
mdb.models[*name*].ContactExp
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which this contact interaction is created.

**Optional arguments**

*useAllstar*

A Boolean specifying whether the contacting surface pair consists of all exterior faces, shell edges, beam segments, analytical rigid surfaces, and when applicable, Eulerian material surfaces.

*globalSmoothing*

A Boolean specifying whether surface smoothing (geometric correction) is automatically applied to all eligible surfaces. The default value is ON.

*includedPairs*

A [RegionPairs](pt01ch25pyo59.md) object specifying the domain pairs included in contact.

*excludedPairs*

A [RegionPairs](pt01ch25pyo59.md) object specifying the domain pairs excluded from contact.

*contactPropertyAssignments*

A [ContactPropertyAssignment](pt01ch25pyo22.md) object specifying the contact property assignments in the contact domain.

*surfaceThicknessAssignments*

A [SurfaceThicknessAssignment](pt01ch25pyo73.md) object specifying the surface thickness assignments in the contact domain.

*surfaceOffsetAssignments*

A [SurfaceOffsetAssignment](pt01ch25pyo72.md) object specifying the surface offset fraction assignments in the contact domain.

*surfaceFeatureAssignments*

A [SurfaceFeatureAssignment](pt01ch25pyo71.md) object specifying the surface feature angle assignments in the contact domain.

*smoothingAssignments*

A [SmoothingAssignment](pt01ch25pyo64.md) object specifying the surface smoothing assignments in the contact domain.

*masterSlaveAssignments*

A [MasterSlaveAssignment](pt01ch25pyo50.md) object specifying the master-slave assignments in the contact domain.

**Return value**

A ContactExp object.

**Exceptions**

None.

### 25.19.2 ContactExp(...)

This method creates a ContactExp object.

**Path**

```
mdb.models[*name*].ContactExp
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which this contact interaction is created.

**Optional arguments**

*globalSmoothing*

A Boolean specifying whether surface smoothing (geometric correction) is automatically applied to all eligible surfaces. The default value is ON.

*useAllstar*

A Boolean specifying whether the contacting surface pair consists of all exterior faces, shell edges, beam segments, analytical rigid surfaces, and when applicable, Eulerian material surfaces.

*includedPairs*

A sequence of pairs of [Region](pt01ch45pyo03.md) objects or SymbolicConstants that specifies the surface pairs in contact. Possible values of the SymbolicConstants are ALLSTAR and SELF. This argument is valid only when *useAllstar*=OFF.

*excludedPairs*

A sequence of pairs of [Region](pt01ch45pyo03.md) objects or SymbolicConstants that specifies the surface pairs excluded from contact. Possible values of the SymbolicConstants are ALLSTAR and SELF.

*contactPropertyAssignments*

A sequence of tuples specifying the properties assigned to each surface pair. Each tuple contains three entries: 
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant GLOBAL.
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant SELF.
- A String specifying an [InteractionProperty](pt01ch25pyo48.md) object associated with this pair of regions.

*surfaceThicknessAssignments*

A sequence of tuples specifying the surface thickness assignments in the contact domain. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface thickness is assigned.
- A Float or a SymbolicConstant specifying the overriding thickness value to be used in the contact definition. Possible values of the SymbolicConstant are ORIGINAL or THINNING.
- A Float specifying a scale factor that multiplies the thickness value specified in the second entry.

*surfaceOffsetAssignments*

A sequence of tuples specifying the surface offset fraction assignments in the contact domain. Each tuple contains two entries: 
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface offset fraction is assigned.
- A Float or a SymbolicConstant specifying the offset fraction value to be used in the contact definition. Possible values of the SymbolicConstant are ORIGINAL, SPOS, or SNEG.

*surfaceFeatureAssignments*

A sequence of tuples specifying the surface feature angle assignments in the contact domain. Each tuple contains two entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface feature angle is assigned.
- A Float or a SymbolicConstant specifying the overriding feature angle value to be used in the contact definition. Possible values of the SymbolicConstant are PERIMETER, ALL, PICKED, or NONE.

*smoothingAssignments*

A sequence of tuples specifying the surface smoothing assignments in the contact domain. Each tuple contains two entries: 
- A region object specifying the surface to which the smoothing option is assigned.
- A SymbolicConstant specifying the smoothing option to be used in the contact definition. Possible values of the SymbolicConstant are NONE, REVOLUTION, SPHERICAL, or TOROIDAL.

*masterSlaveAssignments*

A sequence of tuples specifying pure master-slave assignments in the contact domain. Each tuple contains three entries: 
- A region object or the SymbolicConstant GLOBAL specifying the first surface that defines the master-slave assignment.
- A region object specifying the second surface in the master-slave assignment definition.
- A SymbolicConstant specifying the status of the first surface. Possible values are MASTER and SLAVE.

**Return value**

A ContactExp object.

**Exceptions**

None.

### 25.19.3 Members

The ContactExp object can have the following members:

*name*

A String specifying the repository key.

*globalSmoothing*

A Boolean specifying whether surface smoothing (geometric correction) is automatically applied to all eligible surfaces. The default value is ON.

*includedPairs*

A [RegionPairs](pt01ch25pyo59.md) object specifying the domain pairs included in contact.

*excludedPairs*

A [RegionPairs](pt01ch25pyo59.md) object specifying the domain pairs excluded from contact.

*contactPropertyAssignments*

A [ContactPropertyAssignment](pt01ch25pyo22.md) object specifying the contact property assignments in the contact domain.

*surfaceThicknessAssignments*

A [SurfaceThicknessAssignment](pt01ch25pyo73.md) object specifying the surface thickness assignments in the contact domain.

*surfaceOffsetAssignments*

A [SurfaceOffsetAssignment](pt01ch25pyo72.md) object specifying the surface offset fraction assignments in the contact domain.

*surfaceFeatureAssignments*

A [SurfaceFeatureAssignment](pt01ch25pyo71.md) object specifying the surface feature angle assignments in the contact domain.

*smoothingAssignments*

A [SmoothingAssignment](pt01ch25pyo64.md) object specifying the surface smoothing assignments in the contact domain.

*masterSlaveAssignments*

A [MasterSlaveAssignment](pt01ch25pyo50.md) object specifying the master-slave assignments in the contact domain.

### 25.19.4 Corresponding analysis keywords

| [*CONTACT](../key/key-link.md#usb-kws-hcontact) |
| --- |




