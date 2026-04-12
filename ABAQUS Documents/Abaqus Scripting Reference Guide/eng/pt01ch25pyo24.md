# 25.24 ContactStd object







The ContactStd object defines the contact domain and associated properties during contact in an Abaqus/Standard analysis.

The ContactStd object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.24.1 ContactStd(...)

This method creates a ContactStd object.

**Path**

```
mdb.models[*name*].ContactStd
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which this contact interaction is created.

**Optional arguments**

*useAllstar*

A Boolean specifying whether the contacting surface pairs consist of all exterior faces in the model.

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

*masterSlaveAssignments*

A [MasterSlaveAssignment](pt01ch25pyo50.md) object specifying the master-slave assignments in the contact domain.

*initializationAssignments*

An [InitializationAssignment](pt01ch25pyo47.md) object specifying the contact initialization assignments in the contact domain.

*stabilizationAssignments*

A [StabilizationAssignment](pt01ch25pyo65.md) object specifying the contact stabilization assignments in the contact domain.

*smoothingAssignments*

A [SmoothingAssignment](pt01ch25pyo64.md) object specifying the surface smoothing assignments in the contact domain.

**Return value**

A ContactStd object.

**Exceptions**

None.

### 25.24.2 ContactStd(...)

This method creates a ContactStd object.

**Path**

```
mdb.models[*name*].ContactStd
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

A Boolean specifying whether the contacting surface pairs consist of all exterior faces in the model.

*includedPairs*

A sequence of pairs of [Region](pt01ch45pyo03.md) objects or SymbolicConstants that specifies the surface pairs in contact. Possible values of the SymbolicConstants are ALLSTAR and SELF. This argument is valid only when *useAllstar*=OFF.

*excludedPairs*

A sequence of pairs of [Region](pt01ch45pyo03.md) objects or SymbolicConstants that specifies the surface pairs excluded from contact. Possible values of the SymbolicConstants are ALLSTAR and SELF.

*contactPropertyAssignments*

A sequence of tuples specifying the properties assigned to each surface pair. Each tuple contains three entries: 
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant GLOBAL.
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant SELF.
- A String specifying an [InteractionProperty](pt01ch25pyo48.md) object associated with this pair of regions.

*surfaceFeatureAssignments*

A sequence of tuples specifying the surface feature angle assignments in the contact domain. Each tuple contains two entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface feature angle is assigned.
- A Float or a SymbolicConstant specifying the overriding feature angle value to be used in the contact definition. Possible values of the SymbolicConstant are PERIMETER or NONE.

*surfaceThicknessAssignments*

A sequence of tuples specifying the surface thickness assignments in the contact domain. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface thickness is assigned.
- A Float or a SymbolicConstant specifying the overriding thickness value to be used in the contact definition. The SymbolicConstant ORIGINAL may be specified instead of a floating point value.
- A Float specifying a scale factor that multiplies the thickness value specified in the second entry.

*surfaceOffsetAssignments*

A sequence of tuples specifying the surface offset fraction assignments in the contact domain. Each tuple contains two entries: 
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the surface offset fraction is assigned.
- A Float or a SymbolicConstant specifying the offset fraction value to be used in the contact definition. Possible values of the SymbolicConstant are ORIGINAL, SPOS, or SNEG.

*masterSlaveAssignments*

A sequence of tuples specifying master-slave assignments in the contact domain. Each tuple contains three entries: 
- A region object or the SymbolicConstant GLOBAL specifying the first surface that defines the master-slave assignment.
- A region object specifying the second surface in the master-slave assignment definition.
- A SymbolicConstant specifying the status of the first surface. Possible values are MASTER, SLAVE, and BALANCED.

*initializationAssignments*

A sequence of tuples specifying the contact initialization data assigned to each surface pair. Each tuple contains three entries: 
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant GLOBAL.
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant SELF.
- A String specifying a [StdInitialization](pt01ch25pyo67.md) object associated with this pair of regions.

*stabilizationAssignments*

A sequence of tuples specifying the contact stabilization assigned to each surface pair. Each tuple contains three entries: 
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant GLOBAL.
- A [Region](pt01ch45pyo03.md) object or the SymbolicConstant SELF.
- A String specifying a [StdStabilization](pt01ch25pyo68.md) object associated with this pair of regions.

*smoothingAssignments*

A sequence of tuples specifying the surface smoothing assignments in the contact domain. Each tuple contains two entries: 
- A region object specifying the surface to which the smoothing option is assigned.
- A SymbolicConstant specifying the smoothing option to be used in the contact definition. Possible values of the SymbolicConstant are NONE, REVOLUTION, SPHERICAL, or TOROIDAL.

**Return value**

A ContactStd object.

**Exceptions**

None.

### 25.24.3 Members

The ContactStd object can have the following members:

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

*masterSlaveAssignments*

A [MasterSlaveAssignment](pt01ch25pyo50.md) object specifying the master-slave assignments in the contact domain.

*initializationAssignments*

An [InitializationAssignment](pt01ch25pyo47.md) object specifying the contact initialization assignments in the contact domain.

*stabilizationAssignments*

A [StabilizationAssignment](pt01ch25pyo65.md) object specifying the contact stabilization assignments in the contact domain.

*smoothingAssignments*

A [SmoothingAssignment](pt01ch25pyo64.md) object specifying the surface smoothing assignments in the contact domain.

*surfaceFeatureAssignments*

A [SurfaceFeatureAssignment](pt01ch25pyo71.md) object specifying the surface feature angle assignments in the contact domain.

### 25.24.4 Corresponding analysis keywords

| [*CONTACT](../key/key-link.md#usb-kws-hcontact) |
| --- |




