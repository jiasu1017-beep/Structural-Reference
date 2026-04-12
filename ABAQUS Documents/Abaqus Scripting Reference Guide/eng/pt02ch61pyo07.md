# 61.7 FieldOutput object







A FieldOutput               object contains field data for a specific output variable.

**Access**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*]
```

### 61.7.1 FieldOutput(...)

This method creates a FieldOutput                     object.

**Path**

```
odb.steps()[*name*].frames(*i*).FieldOutput
```

**Prototype**

```
odb_FieldOutput&
FieldOutput(const odb_String& name,
            const odb_String& description,
            odb_Enum::odb_DataTypeEnum type,
            const odb_SequenceString& componentLabels,
            const odb_SequenceInvariant& validInvariants,
            bool isEngineeringTensor);
```

**Required arguments**

*name*

An odb_String specifying the output variable name.

*description*

An odb_String specifying the output variable. Colon (:) should not be used as a part of the field output description.

*type*

An odb_Enum::odb_DataTypeEnum specifying the output type. Possible values are odb_Enum::SCALAR, odb_Enum::VECTOR, odb_Enum::TENSOR_3D_FULL, odb_Enum::TENSOR_3D_PLANAR, odb_Enum::TENSOR_3D_SURFACE, odb_Enum::TENSOR_2D_PLANAR, and odb_Enum::TENSOR_2D_SURFACE.

**Optional arguments**

*componentLabels*

An odb_SequenceString specifying the labels for each component of the value. The length of the sequence must match the type. If *type*=odb_Enum::TENSOR, the default value is *name* with the suffixes ('11', '22', '33', '12', '13', '23'). If *type*=odb_Enum::VECTOR, the default value is *name*                       with the suffixes ('1', '2', '3'). If *type*=odb_Enum::SCALAR, the default value is an empty sequence.

*validInvariants*

An odb_SequenceInvariant specifying which invariants should be calculated for this field. An empty sequence indicates that no invariants are valid for this field. Possible values are:
- odb_Enum::MAGNITUDE
- odb_Enum::MISES
- odb_Enum::TRESCA
- odb_Enum::PRESS
- odb_Enum::INV3
- odb_Enum::MAX_PRINCIPAL
- odb_Enum::MID_PRINCIPAL
- odb_Enum::MIN_PRINCIPAL
- odb_Enum::MAX_INPLANE_PRINCIPAL
- odb_Enum::MIN_INPLANE_PRINCIPAL
- odb_Enum::OUTOFPLANE_PRINCIPAL

The default value is an empty sequence.

*isEngineeringTensor*

A Boolean specifying whether the field is an engineering tensor or not.  Setting isEngineeringTensor to true makes a tensor field behave as a strain like quantity where the off-diagonal components of tensor are halved for invariants computation. This parameter applies only to tensor field outputs. The default value is false.

**Return value**

A FieldOutput object.

**Exceptions**

None.

### 61.7.2 FieldOutput(...)

This method creates a FieldOutput                     object from an existing FieldOutput                     object.

**Path**

```
odb.steps()[*name*].frames(*i*).FieldOutput
```

**Prototype**

```
odb_FieldOutput&
FieldOutput(const odb_FieldOutput& field,
            const odb_String& name,
            const odb_String& description);
```

**Required argument**

*field*

A FieldOutput                              object.

**Optional arguments**

*name*

A String specifying the name of the FieldOutput                              object.

*description*

An odb_String specifying the output variable. Colon (:) should not be used as a part of the field output description.

**Return value**

A FieldOutput object.

**Exceptions**

None.

### 61.7.3 VectorOutput(...)

This method creates a FieldOutput                     object.

**Path**

```
odb.steps()[                      *name*                      ].frames(                      *i*                      ).VectorOutput                   
```

**Prototype**

```
odb_FieldOutput&
VectorOutput(const odb_String& name,
             const odb_String& description,
             int width);
```

**Required arguments**

*name*

An odb_String specifying the output variable name.

*description*

An odb_String specifying the output variable. Colon (:) should not be used as a part of the field output description.

*width*

An Int specifying the width of the vector.

**Optional arguments**

None.

**Return value**

A FieldOutput                     object.

**Exceptions**

None.

### 61.7.4 MatrixOutput(...)

This method creates a FieldOutput                     object.

**Path**

```
odb.steps()[                      *name*                      ].frames(                      *i*                      ).MatrixOutput                   
```

**Prototype**

```
odb_FieldOutput&
MatrixOutput(const odb_String& name,
             const odb_String& description,
             int rows,
             int cols);
```

**Required arguments**

*name*

An odb_String specifying the output variable name.

*description*

An odb_String specifying the output variable. Colon (:) should not be used as a part of the field output description.

*rows*

An Int specifying the number of rows in the matrix.

*cols*

An Int specifying the number of columns in the matrix.

**Optional arguments**

None.

**Return value**

A FieldOutput                     object.

**Exceptions**

None.

### 61.7.5 SymmetricMatrixOutput(...)

This method creates a FieldOutput                     object.

**Path**

```
odb.steps()[                      *name*                      ].frames(                      *i*                      ).SymmetricMatrixOutput                   
```

**Prototype**

```
odb_FieldOutput&
SymmetricMatrixOutput(const odb_String& name,
                      const odb_String& description,
                      int dim);
```

**Required arguments**

*name*

An odb_String specifying the output variable name.

*description*

An odb_String specifying the output variable. Colon (:) should not be used as a part of the field output description.

*dim*

An Int specifying the dimension of the symmetric matrix.

**Optional arguments**

None.

**Return value**

A FieldOutput                     object.

**Exceptions**

None.

### 61.7.6 addData(...)

This method adds data to a FieldOutput                     object.

**Prototype**

```
void
addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Instance& instance,
        const odb_SequenceInt& labels,
        const odb_SequenceSequenceFloat& data,
        const odb_SectionPoint& sectionPoint,
        const odb_SequenceSequenceFloat& localCoordSystem,
        const odb_SequenceSequenceFloat& conjugateData);
```

**Required arguments**

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*instance*

An [OdbInstance](pt02ch61pyo16.md)                              object specifying the namespace for labels.

*labels*

An odb_SequenceInt specifying the labels of the nodes or elements where the values in *data*                                are located. The node or element labels must be sorted in ascending order and must be specified in the same order as the values provided for the *data*                                argument. 

*data*

An odb_SequenceSequenceFloat specifying the data values for the specified *position*, *instance*, and *labels*. The values must be given in the correct order. Element nodal data follow the order of nodal connectivity defined in the Abaqus documentation. Integration point data follow the order defined in the Abaqus documentation. Section point data for beams and shells follow the convention given in the Abaqus documentation. For more information, see [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). These data create [FieldValue](pt02ch61pyo08.md)                                objects internally.

**Optional arguments**

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md)                              object specifying the location in the section. Although *sectionPoint*                                is an optional argument to the `addData`                                method, omitting the argument does have consequences for visualization. If you omit the argument when you are writing field output data for a shell or a beam, you cannot subsequently select the section point to display when you are displaying the field output data using the Visualization module.

*localCoordSystem*

An odb_SequenceSequenceFloat specifying the 3  3 matrix of direction cosines of the local coordinate system. This argument is available only for fields with type=odb_Enum::TENSOR or odb_Enum::VECTOR.

User-supplied values of localCoordSystem are transposed before storing in the database.

*conjugateData*

                  An odb_SequenceSequenceFloat specifying the imaginary data values for the specified position, instance, and labels. You must provide these data when you add complex fields to the output database. The order of the values follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).                

**Return value**

None

**Exceptions**

The `addData`                             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:

```
odbException: Transformation not allowed for scalar data.
```

### 61.7.7 addData(...)

This method adds the data from a field created using the `getSubset`                       method and mathematical operators to the database. The user must create a field to contain the new data and then use the `addData`                       method to assign the data from the fields.

**Prototype**

```
void
addData(const odb_FieldOutput& field);
```

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

### 61.7.8 addData(...)

This method adds data to a FieldOutput                       object.

**Prototype**

```
void
addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Set& set,
        const odb_SequenceSequenceFloat& data,
        const odb_SectionPoint& sectionPoint,
        const odb_SequenceSequenceFloat& conjugateData);
```

**Required arguments**

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.
- odb_Enum::ELEMENT_FACE_INTEGRATION_POINT, specifying the values calculated at the element face integration points.
- odb_Enum::SURFACE_INTEGRATION_POINT, specifying the values calculated at the surface integration points. Selecting this value prompts the Visualization module to calculate the sum of the values at the ELEMENT_FACE_INTEGRATION_POINT position from multiple surfaces.

*set*

An [OdbSet](pt02ch61pyo24.md)                              object specifying the instance-level set defining the region for `addData`. The set must be defined in the same output database as the output database into which the new field output data is being written. The node or element labels in the set must be sorted in ascending order and must be specified in the same order as the values provided for the *data*                                argument. 

*data*

An odb_SequenceSequenceFloat specifying the data values for the specified position and labels in the set. Each row of data provides the value at one unique position. The width of each row should match the number of required components for the data. The values must be given in the order that matches the ordering of labels in the set.

The order of the element nodal data, integration point data, and section point data for beams and shells follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).”

**Optional arguments**

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md) object specifying the location in the section. Although *sectionPoint* is an optional argument to the`addData` method, omitting the argument does have consequences for visualization. If you omit the argument when you are writing field output data for a shell or a beam, you cannot subsequently select the section point to display when you are displaying the field output data using the Visualization module.

*conjugateData*

An odb_SequenceSequenceFloat specifying the imaginary data values for the specified position, instance, and labels. You must provide this data when you add complex fields to the output database. The order of the values follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

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

### 61.7.9 addData(...)

         This method adds data to a FieldOutput                     object.       

**Prototype**

```

        void
        addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Instance& instance,
        const odb_SequenceInt& labels,
        const odb_SequenceSequenceFloat& data,
        const odb_SectionPoint& sectionPoint,
        const odb_SequenceSequenceSequenceFloat& localCoordSystem,
        const odb_SequenceSequenceFloat& conjugateData);

```

**Required arguments**

*position*

               An odb_Enum::odb_ResultPositionEnum specifying the position of the output. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*instance*

               An [OdbInstance](pt02ch61pyo16.md)                              object specifying the namespace for labels.             

*labels*

               An odb_SequenceInt specifying the labels of the nodes or elements where the values in *data*               are located. The node or element labels must be sorted in ascending order and must be specified in the same order as the values provided for the *data*               argument.             

*data*

               An odb_SequenceSequenceFloat specifying the data values for the specified *position*, *instance*, and *labels*. The values must be given in the correct order. Element nodal data follow the order of nodal connectivity defined in the Abaqus documentation. Integration point data follow the order defined in the Abaqus documentation. Section point data for beams and shells follow the convention given in the Abaqus documentation. For more information, see [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). These data create [FieldValue](pt02ch61pyo08.md)               objects internally.             

**Optional arguments**

*sectionPoint*

               A [SectionPoint](pt02ch61pyo28.md)                              object specifying the location in the section. Although *sectionPoint*               is an optional argument to the `addData`               method, omitting the argument does have consequences for visualization. If you omit the argument when you are writing field output data for a shell or a beam, you cannot subsequently select the section point to display when you are displaying the field output data using the Visualization module.             

*localCoordSystem*

An odb_SequenceSequenceSequenceFloat specifying the direction cosines of the local coordinates systems, where the sequence is the same length as *data*. When specified this way a different local coordinate system applies to each data value.                                           

User-supplied values of localCoordSystem are transposed before storing in the database.

*conjugateData*

               An odb_SequenceSequenceFloat specifying the imaginary data values for the specified *position*, *instance*, and *labels*. You must provide this data when you add complex fields to the output database. The order of the values follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).             

**Return value**

None

**Exceptions**

             The `addData`             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:           

```
odbException: Transformation not allowed for scalar data.
```

### 61.7.10 addData(...)

         This method adds double precision data to a FieldOutput                     object.       

**Prototype**

```

        void
        addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Instance& instance,
        const odb_SequenceInt& labels,
        const odb_SequenceSequenceDouble& data,
        const odb_SequenceSequenceSequenceDouble& localCoordSystem,
        const odb_SequenceSequenceDouble& conjugateData);      
```

**Required arguments**

*position*

               An odb_Enum::odb_ResultPositionEnum specifying the position of the output. Only odb_Enum::NODAL, specifying the values calculated at the nodes, is supported.

*instance*

               An [OdbInstance](pt02ch61pyo16.md)                              object specifying the namespace for labels.             

*labels*

               An odb_SequenceInt specifying the labels of the nodes or elements where the values in *data*               are located. The node or element labels must be sorted in ascending order and must be specified in the same order as the values provided for the *data*               argument.             

*data*

               An odb_SequenceSequenceDouble specifying the data values for the specified *position*, *instance*, and *labels*. The values must be given in the correct order. These data create [FieldValue](pt02ch61pyo08.md)               objects internally.             

**Optional arguments**

*localCoordSystem*

An odb_SequenceSequenceSequenceDouble specifying the direction cosines of the local coordinates systems, where the sequence is the same length as *data*. When specified this way a different local coordinate system applies to each data value.                                           

User-supplied values of localCoordSystem are transposed before storing in the database.

*conjugateData*

               An odb_SequenceSequenceDouble specifying the imaginary data values for the specified *position*, *instance*, and *labels*. You must provide this data when you add complex fields to the output database. The order of the values follows the conventions defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).             

**Return value**

None

**Exceptions**

             The `addData`             method throws many exceptions of type odbException. For example, if the local coordinate system is specified for scalar data:           

```
odbException: Transformation not allowed for scalar data.
```

### 61.7.11 getScalarField(...)

This method generates a scalar field containing the extracted component or calculated invariant values. The new field will hold values for the same nodes or elements as the parent field. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Prototype**

```
odb_FieldOutput
getScalarField(odb_Enum::odb_InvariantEnum invariant);
```

**Required argument**

*invariant*

An odb_Enum::odb_InvariantEnum specifying the invariant. Possible values areodb_Enum::MAGNITUDE, odb_Enum::MISES, odb_Enum::TRESCA, odb_Enum::PRESS, odb_Enum::INV3, odb_Enum::MAX_PRINCIPAL, odb_Enum::MID_PRINCIPAL, odb_Enum::MIN_PRINCIPAL, odb_Enum::MAX_INPLANE_PRINCIPAL, odb_Enum::MIN_INPLANE_PRINCIPAL, and odb_Enum::OUTOFPLANE_PRINCIPAL.

**Optional arguments**

None.

**Return value**

AFieldOutput                     object.

**Exceptions**

None.

### 61.7.12 getScalarField(...)

This method generates a scalar field containing the extracted component or calculated invariant values. The new field will hold values for the same nodes or elements as the parent field. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Prototype**

```
odb_FieldOutput
getScalarField(const odb_String& componentLabel);
```

**Required argument**

*componentLabel*

A String specifying the component label, such as “S11”.

**Optional arguments**

None.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.13 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(odb_Enum::odb_ResultPositionEnum position,
          bool readOnly);
```

**Required arguments**

None.

**Optional arguments**

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output in the element. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

                              If the requested field values are not found in the output database at the specified odb_Enum::ELEMENT_NODAL                                or odb_Enum::CENTROID                                positions, they are extrapolated from the field data at the odb_Enum::INTEGRATION_POINT                                position.

*readOnly*

A Boolean specifying whether the extrapolated data returned by this call is written to the output database.  The default value is false.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.14 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_Set& region);
```

**Required arguments**

None.

**Optional argument**

*region*

An [OdbSet](pt02ch61pyo24.md)                                specifying the region for which to extract values. Nodes or elements in the sets must be sorted and arranged in ascending order. Use of unsorted sets is not supported. This is especially true for sets in Abaqus output databases obtained through running the analysis in multiple domains. In such cases, a new sorted set must be created before using it in the getSubset method.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.15 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_SequenceSequenceFloat& localCoordSystem);
```

**Required arguments**

None.

**Optional argument**

*localCoordSystem*

An odb_SequenceSequenceFloat specifying the 3  3 matrix of direction cosines. Field values associated with the supplied coordinate system will be extracted.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.16 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_SectionPoint& sectionPoint);
```

**Required arguments**

None.

**Optional argument**

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md)                                object.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.17 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_FieldLocation& location);
```

**Required arguments**

None.

**Optional argument**

*location*

A [FieldLocation](pt02ch61pyo06.md)                                object.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.18 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_Element& region);
```

**Required arguments**

None.

**Optional argument**

*region*

An [OdbMeshElement](pt02ch61pyo18.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.19 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_Node& region);
```

**Required arguments**

None.

**Optional argument**

*region*

An [OdbMeshNode](pt02ch61pyo19.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.20 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_Instance& region);
```

**Required arguments**

None.

**Optional argument**

*region*

An [OdbInstance](pt02ch61pyo16.md)                                specifying the region for which to extract values.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.21 getSubset(...)

A FieldOutput                       object with a subset of the field values.

**Prototype**

```
odb_FieldOutput
getSubset(const odb_String& elementType);
```

**Required arguments**

None.

**Optional argument**

*elementType*

A String specifying the element type for which to extract values. The string must correspond to a valid Abaqus element type.

**Return value**

A FieldOutput                       object.

**Exceptions**

None.

### 61.7.22 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](#ker-datumcsys-cpp)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Prototype**

```
odb_FieldOutput
getTransformedField(const odb_DatumCsys& datumCsys,
                    int projected22Axis,
                    double projectionTol);
```

**Required argument**

*datumCsys*

A valid [DatumCsys](#ker-datumcsys-cpp)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

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

### 61.7.23 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](#ker-datumcsys-cpp)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Prototype**

```
odb_FieldOutput
getTransformedField(const odb_DatumCsys& datumCsys,
                    const odb_FieldOutput& deformationField,
                    int projected22Axis,
                    double projectionTol);
```

**Required argument**

*datumCsys*

A valid [DatumCsys](#ker-datumcsys-cpp)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

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

### 61.7.24 getTransformedField(...)

This method generates a new vector or tensor field containing the transformed component values of the parent field. The new field will hold values for the same nodes or elements as the parent field. Results will be transformed based on the orientations specified by the input [DatumCsys](#ker-datumcsys-cpp)                       object. Abaqus will perform this operation on only the real part of the FieldOutput                       object. The operation is not performed on the conjugate data (the imaginary portion of a complex result).

**Prototype**

```
odb_FieldOutput
getTransformedField(const odb_DatumCsys& datumCsys,
                    const odb_FieldOutput& deformationField,
                    const odb_FieldOutput& rotationField,
                    int projected22Axis,
                    double projectionTol);
```

**Required argument**

*datumCsys*

A valid [DatumCsys](#ker-datumcsys-cpp)                                object designating the coordinate system. Valid systems can be fixed or positioned with respect to nodes on the model and can be cartesian, cylindrical, or spherical.

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

### 61.7.25 Members

The FieldOutput object has members with the same names and descriptions as the arguments to the [FieldOutput](pt02ch61pyo07.md#ker-fieldoutput-fieldoutput-cpp) method.

In addition, the FieldOutput object can have the following members:

**Prototype**

```
odb_String name() const;
               odb_String description() const;
               odb_Enum::odb_DataTypeEnum type() const;
               odb_Enum::odb_DataSubtypeEnum subtype() const;
               int dim() const;
               int dim2() const;
               bool isComplex() const;
               odb_SequenceInvariant validInvariants() const;
               odb_SequenceString componentLabels() const;
               odb_SequenceString baseElementTypes() const;
               const odb_SequenceFieldLocation& locations() const;
               odb_FieldLocation locations(int index) const;
               const odb_FieldValue values(int i);
               odb_SequenceFieldValue values();
               const odb_FieldBulkData& bulkDataBlocks(int i);
               odb_SequenceFieldBulkData& bulkDataBlocks();
```

*dim*

An Int specifying the dimension of vector or the first dimension (number of rows) of matrix.

*dim2*

An Int specifying the second dimension (number of columns) of matrix.

*isComplex*

A Boolean specifying whether the data are complex.

*locations*

A sequence of [FieldLocation](pt02ch61pyo06.md) objects.

*values*

A sequence of [FieldValue](pt02ch61pyo08.md) objects specifying the order of the objects in the array is determined by the Abaqus Scripting Interface; see the *data*                       argument to the `addData`                       method for a description of the order.

*bulkDataBlocks*

A sequence of [FieldBulkData](pt02ch61pyo05.md) objects.




