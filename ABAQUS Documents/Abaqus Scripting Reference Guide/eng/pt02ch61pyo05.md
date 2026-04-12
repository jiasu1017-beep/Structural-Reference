# 61.5 FieldBulkData object







The FieldBulkData                 object represents the entire field data for a class of elements or nodes. All elements in a class correspond to the same element type and material.

**Access**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].bulkDataBlocks(*i*)
```

### 61.5.1 Members

The FieldBulkData object can have the following members:

**Prototype**

```
odb_Enum::odb_ResultPositionEnum position() const;
               odb_Enum::odb_PrecisionEnum precision() const;
               int* elementLabels() const;
               int* nodeLabels() const;
               int* integrationPoints() const;
               odb_String baseElementType() const;
               odb_Enum::odb_ElementFaceEnum* faces() const;
               odb_Enum::odb_DataTypeEnum type() const;
               float* data() const;
               double* dataDouble() const;
               float* conjugateData() const;
               double* conjugateDataDouble() const;
               float* mises() const;
               float* localCoordSystem() const;
               double* localCoordSystemDouble() const;
               int orientationWidth() const;
               int numberOfElements() const;
               int length() const;
               int valuesPerElement() const;
               int width() const;
               const odb_Instance& instance() const;
               const odb_SectionPoint& sectionPoint() const;
               odb_SequenceString componentLabels() const;
```

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::ELEMENT_FACE, specifying the results obtained for surface variables such as cavity radiation that are defined for the surface facets of an element.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*precision*

An odb_Enum::odb_PrecisionEnum specifying the precision of the output. Possible values are:
- odb_Enum::SINGLE_PRECISION, specifying that the output is in single precision.
- odb_Enum::DOUBLE_PRECISION, specifying that the output is in double precision.

*type*

An odb_Enum::odb_DataTypeEnum specifying the output type. Possible values are odb_Enum::SCALAR, odb_Enum::VECTOR, odb_Enum::TENSOR_3D_FULL, odb_Enum::TENSOR_3D_PLANAR, odb_Enum::TENSOR_3D_SURFACE, odb_Enum::TENSOR_2D_PLANAR, and odb_Enum::TENSOR_2D_SURFACE.

*orientationWidth*

An Int specifying the number of direction cosines necessary to specify the local coordinate system at each output location. You use *orientationWidth*                    to read the orientation data from the *localCoordSystem*.

*numberOfElements*

An Int specifying the number of elements in the current block of data.

*length*

An Int specifying the number of output locations in the current block of data.

*valuesPerElement*

An Int specifying the number of values per element in the current block of data. If *position*=odb_Enum::ELEMENT_NODAL, *valuesPerElement*                    is the number of nodes per element for all elements in the current block of data.

*width*

An Int specifying the number of components at each output location.

*baseElementType*

An odb_String specifying the element type corresponding to the current block of data.

*instance*

An [OdbInstance](pt02ch61pyo16.md) object specifying the part to which the labels belong.

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md) object specifying the section point number of the current block of data.

*elementLabels*

A pointer to an array of Ints specifying the element labels of the elements in the block. *elementLabels*                       is valid only if *position*                     =odb_Enum::INTEGRATION_POINT                     , odb_Enum::CENTROID                     , odb_Enum::ELEMENT_NODAL                     , or odb_Enum::ELEMENT_FACE. If *position*                     =odb_Enum::NODAL                     , *elementLabels*                       returns a NULL pointer.

*nodeLabels*

A pointer to an array of Ints specifying the node labels of the nodes in the block. *nodeLabels*                       is valid only if *position*                     =odb_Enum::NODAL                       or odb_Enum::ELEMENT_NODAL. If *position*                     =odb_Enum::INTEGRATION_POINT                     , odb_Enum::CENTROID                     , odb_Enum::ELEMENT_NODAL                     , or odb_Enum::ELEMENT_FACE                     , *nodeLabels*                       returns a NULL pointer.

*integrationPoints*

A pointer to an array of Ints specifying the integration points in the elements in the block. *integrationPoint*                       is available only if *position*                     =odb_Enum::INTEGRATION_POINT.

*faces*

A pointer to an array of odb_Enum::odb_ElementFaceEnum enumerations specifying the faces of the elements in the block. *faces*                       is available only if *position*                     =odb_Enum::ELEMENT_FACE.

*data*

A pointer to an array of Floats specifying the field's data in the order described by *type*. If *type* = odb_Enum::TENSOR                       or odb_Enum::VECTOR, *data*                       is an array containing the components for each element or node in the block. If the underlying data are in double precision, an exception will be thrown.

*dataDouble*

A pointer to an array of Doubles specifying the field's data in the order described by *type*. If *type* = odb_Enum::TENSOR                     or odb_Enum::VECTOR, *data*                       is an array containing the components for each element or node in the block. If the underlying data are in single precision, an exception will be thrown.

*conjugateData*

A pointer to an array of Floats specifying the imaginary portion of a complex result. The order of the Floats is described by*type*. If *type* = odb_Enum::TENSOR                     or odb_Enum::VECTOR, *conjugateData*                       is an array containing the imaginary part of the components for each element or node in the block. If the underlying data are in double precision, an exception will be thrown.

*conjugateDataDouble*

A pointer to an array of Doubles specifying the imaginary portion of a complex result. The order of the Doubles is described by *type*. If *type* = odb_Enum::TENSOR                     or odb_Enum::VECTOR, *conjugateData*                       is an array containing the imaginary part of the components for each element or node in the block. If the underlying data are in single precision, an exception will be thrown.

*mises*

A pointer to an array of Floats specifying the calculated von Mises stress at each output location in the block of element data, or NULL. If *validInvariants*                       includes odb_Enum::MISES, *mises*                       returns an array pointer. If *validInvariants*                       does not include odb_Enum::MISES, *mises*                       returns a NULL pointer.  Conjugate data will be ignored in invariant calculation.

*localCoordSystem*

A pointer to an array of Floats specifying the quaternion representing the local coordinate system at each output location. The quaternion is returned in the form ![](../graphics/ker_eqn00435.gif), which is the reverse of that shown in ["Rotation variables," Section 1.3.1 of the Abaqus Theory Guide](../stm/stm-link.md#stm-int-rotationvars). *localCoordSystem*                       is available only for odb_Enum::TENSOR                       data written in a local coordinate system. If the underlying data are in double precision, an exception will be thrown.

*localCoordSystemDouble*

A pointer to an array of Doubles specifying the quaternion representing the local coordinate system at each output location.  The quaternion is returned in the form ![](../graphics/ker_eqn00436.gif) , which is the reverse of that shown in ["Rotation variables," Section 1.3.1 of the Abaqus Theory Guide](../stm/stm-link.md#stm-int-rotationvars). *localCoordSystemDouble*                       is available only for odb_Enum::TENSOR                       data written in a local coordinate system. If the underlying data are in single precision, an exception will be thrown.

*componentLabels*

An odb_SequenceString specifying the component labels.




