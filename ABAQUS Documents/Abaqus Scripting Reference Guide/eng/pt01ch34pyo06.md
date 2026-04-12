# 34.6 FieldOutput object







A FieldOutput               object contains field data for a specific output variable.

**Access**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*]
```

### 34.6.1 FieldOutput(...)

This method creates a FieldOutput                     object.

**Path**

```
session.odbs[*name*].steps[*name*].frames[*i*].FieldOutput
```

**Required arguments**

*name*

A String specifying the output variable name.

*description*

A String specifying the output variable. Colon (:) should not be used as a part of the field output description.

*type*

A SymbolicConstant specifying the output type. Possible values are SCALAR, VECTOR, TENSOR_3D_FULL, TENSOR_3D_PLANAR, TENSOR_3D_SURFACE, TENSOR_2D_PLANAR, and TENSOR_2D_SURFACE.

**Optional arguments**

*componentLabels*

A sequence of Strings specifying the labels for each component of the value. The length of the sequence must match the type. If *type*=TENSOR, the default value is *name* with the suffixes ('11', '22', '33', '12', '13', '23'). If *type*=VECTOR, the default value is *name*                       with the suffixes ('1', '2', '3'). If *type*=SCALAR, the default value is an empty sequence.

*validInvariants*

A sequence of SymbolicConstants specifying which invariants should be calculated for this field. An empty sequence indicates that no invariants are valid for this field. Possible values are:
- MAGNITUDE
- MISES
- TRESCA
- PRESS
- INV3
- MAX_PRINCIPAL
- MID_PRINCIPAL
- MIN_PRINCIPAL
- MAX_INPLANE_PRINCIPAL
- MIN_INPLANE_PRINCIPAL
- OUTOFPLANE_PRINCIPAL

The default value is an empty sequence.

*isEngineeringTensor*

A Boolean specifying whether the field is an engineering tensor or not.  Setting isEngineeringTensor to true makes a tensor field behave as a strain like quantity where the off-diagonal components of tensor are halved for invariants computation. This parameter applies only to tensor field outputs. The default value is OFF.

**Return value**

A FieldOutput object.

**Exceptions**

None.

### 34.6.2 FieldOutput(...)

This method creates a FieldOutput                     object from an existing FieldOutput                     object.

**Path**

```
session.odbs[*name*].steps[*name*].frames[*i*].FieldOutput
```

**Required argument**

*field*

A FieldOutput                              object.

**Optional arguments**

*name*

A String specifying the name of the FieldOutput                              object.

*description*

A String specifying the output variable. Colon (:) should not be used as a part of the field output description.

**Return value**

A FieldOutput object.

**Exceptions**

None.

### 34.6.3 addData(...)

This method adds data to a FieldOutput                     object.

**Required arguments**

*position*

A SymbolicConstant specifying the position of the output. Possible values are:
- NODAL, specifying the values calculated at the nodes.
- INTEGRATION_POINT, specifying the values calculated at the integration points.
- ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*instance*

An [OdbInstance](pt01ch34pyo15.md)                              object specifying the namespace for labels.

*labels*

A sequence of Ints specifying the labels of the nodes or elements where the values in *data*                                are located. The node or element labels must be sorted in ascending order and must be specified in the same order as the values provided for the *data*                                argument. 

*data*

A sequence of sequences of Floats specifying the data values for the specified *position*, *instance*, and *labels*. The values must be given in the correct order. Element nodal data follow the order of nodal connectivity defined in the Abaqus documentation. Integration point data follow the order defined in the Abaqus documentation. Section point data for beams and shells follow the convention given in the Abaqus documentation. For more information, see [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). These data create [FieldValue](pt01ch34pyo07.md)                                objects internally.

**Optional arguments**

*sectionPoint*

A [SectionPoint](pt01ch34pyo28.md)                              object specifying the location in the section. Although *sectionPoint*                                is an optional argument to the `addData`                                method, omitting the argument does have consequences for visualization. If you omit the argument when you are writing field output data for a shell or a beam, you cannot subsequently select the section point to display when you are displaying the field output data using the Visualization module.

*localCoordSystem*

                            The *localCoordSystem* parameter can be specified using either of the following:
- A sequence of sequences of Floats specifying the 3 3 matrix of direction cosines of the local coordinate system. This argument is available only for fields with type=TENSOR or VECTOR.
- A sequence of matrices of floats specifying the direction cosines of the local coordinates systems, where the sequence is the same length as *data*. If *localCoordSystem* is a matrix, a different local coordinate system applies to each data value.

			    User supplied values of localCoordSystem are transposed before storing in the database.

**Return value**

None

**Exceptions**

The `addData`                             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.4 addData(...)

This method adds the data from a field created using the `getSubset`                       method and mathematical operators to the database. The user must create a field to contain the new data and then use the `addData`                       method to assign the data from the fields.

**Required argument**

*field*

A FieldOutput                                object specifying the data to add.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

The `addData`                             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.5 addData(...)

This method adds data to a FieldOutput                       object.

**Required arguments**

*position*

A SymbolicConstant specifying the position of the output. Possible values are:
- NODAL, specifying the values calculated at the nodes.
- INTEGRATION_POINT, specifying the values calculated at the integration points.
- ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.
- ELEMENT_FACE_INTEGRATION_POINT, specifying the values calculated at the element face integration points.
- SURFACE_INTEGRATION_POINT, specifying the values calculated at the surface integration points. Selecting this value prompts the Visualization module to calculate the sum of the values at the ELEMENT_FACE_INTEGRATION_POINT position from multiple surfaces.

*set*

An [OdbSet](pt01ch34pyo23.md)                              object specifying the instance-level set defining the region for `addData`. The set must be defined in the same output database as the output database into which the new field output data is being written. The node or element labels in the set must be sorted in ascending order and must be specified in the same order as the values provided for the *data*                                argument. 

*data*

A sequence of sequences of Floats specifying the data values for the specified position and labels in the set. Each row of data provides the value at one unique position. The width of each row should match the number of required components for the data. The values must be given in the order that matches the ordering of labels in the set.

The order of the element nodal data, integration point data, and section point data for beams and shells follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).”

**Optional arguments**

*sectionPoint*

                           A [SectionPoint](pt01ch34pyo28.md)                           object specifying the location in the section. Although*sectionPoint*                           is an optional argument to the`addData`                           method, omitting the argument does have consequences for visualization. If you omit the argument when you are writing field output data for a shell or a beam, you cannot subsequently select the section point to display when you are displaying the field output data using the Visualization module.

*conjugateData*

An odb_SequenceSequenceFloat object specifying the imaginary data values for the specified position, instance, and labels. You must provide this data when you add complex fields to the output database. The order of the values follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

**Return value**

None

**Exceptions**

If you specify an odbSet containing entities from multiple instances:

```
odbException: Entities from multiple instances present in set.
```

The `addData`                             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.6 getScalarField(...)

This method generates a scalar field containing the extracted component or calculated invariant values. The new field will hold values for the same nodes or elements as the parent field. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Required argument**

*invariant*

A SymbolicConstant specifying the invariant. Possible values areMAGNITUDE, MISES, TRESCA, PRESS, INV3, MAX_PRINCIPAL, MID_PRINCIPAL, MIN_PRINCIPAL, MAX_INPLANE_PRINCIPAL, MIN_INPLANE_PRINCIPAL, and OUTOFPLANE_PRINCIPAL.

**Optional arguments**

None.

**Return value**

AFieldOutput                     object.

**Exceptions**

None.

### 34.6.7 getScalarField(...)

This method generates a scalar field containing the extracted component or calculated invariant values. The new field will hold values for the same nodes or elements as the parent field. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Required argument**

*componentLabel*

A String specifying the component label, such as “S11”.

**Optional arguments**

None.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.8 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional arguments**

*position*

A SymbolicConstant specifying the position of the output in the element. Possible values are:
- NODAL, specifying the values calculated at the nodes.
- INTEGRATION_POINT, specifying the values calculated at the integration points.
- ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

                              If the requested field values are not found in the output database at the specified ELEMENT_NODAL                                or CENTROID                                positions, they are extrapolated from the field data at the INTEGRATION_POINT                                position.

*readOnly*

A Boolean specifying whether the extrapolated data returned by this call is written to the output database.  The default value is OFF.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.9 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*region*

An [OdbSet](pt01ch34pyo23.md)                                specifying the region for which to extract values. Nodes or elements in the sets must be sorted and arranged in ascending order. Use of unsorted sets is not supported. This is especially true for sets in Abaqus output databases obtained through running the analysis in multiple domains. In such cases, a new sorted set must be created before using it in the getSubset method.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.10 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*localCoordSystem*

A sequence of sequences of Floats specifying the 3  3 matrix of direction cosines. Field values associated with the supplied coordinate system will be extracted.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.11 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*sectionPoint*

A [SectionPoint](pt01ch34pyo28.md)                                object.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.12 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*location*

A [FieldLocation](pt01ch34pyo05.md)                                object.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.13 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*region*

An [OdbMeshElement](pt01ch34pyo17.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.14 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*region*

An [OdbMeshNode](pt01ch34pyo18.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.15 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*region*

An [OdbInstance](pt01ch34pyo15.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.16 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Required arguments**

None.

**Optional argument**

*elementType*

A String specifying the element type for which to extract values. The string must correspond to a valid Abaqus element type.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 34.6.17 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](pt01ch15pyo03.md)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Required argument**

*datumCsys*

A valid [DatumCsys](pt01ch15pyo03.md)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

**Optional arguments**

*projected22Axis*

An Int specifying which axis of the coordinate system will be projected as the second component for local result orientations. Valid values are 1, 2, or 3; the default value is 2.

*projectionTol*

A Double specifying the minimum allowable angle (radians) between the specified projection axis and the element normal. The next axis will be used for projection if this tolerance test fails.

**Return value**

A FieldOutput                       object.

**Exceptions**

The `getTransformedField`                             method throws an exception if the field contains any assembly level nodes.

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.18 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](pt01ch15pyo03.md)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Required argument**

*datumCsys*

A valid [DatumCsys](pt01ch15pyo03.md)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

**Optional arguments**

*deformationField*

A FieldOutput                                object specifying the nodal displacement vectors required by moving coordinate systems to determine instantaneous configurations.

*projected22Axis*

An Int specifying which axis of the coordinate system will be projected as the second component for local result orientations. Valid values are 1, 2, or 3; the default value is 2.

*projectionTol*

A Double specifying the minimum allowable angle (radians) between the specified projection axis and the element normal. The next axis will be used for projection if this tolerance test fails.

**Return value**

A FieldOutput                       object.

**Exceptions**

The `getTransformedField`                             method throws an exception if the field contains any assembly level nodes.

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.19 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](pt01ch15pyo03.md)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Required argument**

*datumCsys*

A valid [DatumCsys](pt01ch15pyo03.md)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

**Optional arguments**

*deformationField*

A FieldOutput                                object specifying the nodal displacement vectors required by moving coordinate systems to determine instantaneous configurations.

*rotationField*

A FieldOutput                                object specifying the nodal rotational displacement vectors required by moving coordinate systems that follow a 6-dof node, to determine instantaneous configurations.

*projected22Axis*

An Int specifying which axis of the coordinate system will be projected as the second component for local result orientations. Valid values are 1, 2, or 3; the default value is 2.

*projectionTol*

A Double specifying the minimum allowable angle (radians) between the specified projection axis and the element normal. The next axis will be used for projection if this tolerance test fails.

**Return value**

A FieldOutput                       object.

**Exceptions**

The `getTransformedField`                             method throws an exception if the field contains any assembly level nodes.

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.20 Members

The FieldOutput object has members with the same names and descriptions as the arguments to the [FieldOutput](pt01ch34pyo06.md#ker-fieldoutput-fieldoutput-pyc) method.

In addition, the FieldOutput object can have the following members:

*dim*

An Int specifying the dimension of vector or the first dimension (number of rows) of matrix.

*dim2*

An Int specifying the second dimension (number of columns) of matrix.

*isComplex*

A Boolean specifying whether the data are complex.

*locations*

A [FieldLocationArray](pt01ch34pyo05.md) object.

*values*

A [FieldValueArray](pt01ch34pyo07.md) object specifying the order of the objects in the array is determined by the Abaqus Scripting Interface; see the *data*                       argument to the `addData`                       method for a description of the order.




