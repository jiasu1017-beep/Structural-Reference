# 61.8 FieldValue object







The FieldValue object represents the field data at a point. The FieldValue object has no constructor; it is created by the [Odb](pt02ch61pyo01.md) object when data are added to the [FieldOutput](pt02ch61pyo07.md) object using the `addData` method. For faster, bulk-data access, see ["Using bulk data access to an output database," Section 10.10.7 of the Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd-odb-intro-bulkdata-cpp).

**Access**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*)
```

### 61.8.1 Members

The FieldValue object has the following members:

**Prototype**

```
odb_Enum::odb_ResultPositionEnum position() const;
const odb_Instance& instance() const;
int elementLabel() const;
int nodeLabel() const;
int integrationPoint() const;
odb_Enum::odb_ElementFaceEnum face() const;
odb_SectionPoint sectionPoint() const;
odb_Enum::odb_PrecisionEnum precision() const;
odb_Enum::odb_DataTypeEnum type() const;
const float* data(int& numVal) const;
odb_SequenceFloat data() const;
const float* conjugateData(int& numVal) const;
odb_SequenceFloat conjugateData() const;
const double* dataDouble(int& numVal) const;
odb_SequenceDouble dataDouble() const;
const double* conjugateDataDouble(int& numVal) const;
odb_SequenceDouble conjugateDataDouble() const;
odb_SequenceSequenceFloat localCoordSystem() const;
odb_SequenceSequenceDouble localCoordSystemDouble() const;
float magnitude() const;
float mises() const;
float tresca() const;
float press() const;
float inv3() const;
float maxPrincipal() const;
float midPrincipal() const;
float minPrincipal() const;
float maxInPlanePrincipal() const;
float minInPlanePrincipal() const;
float outOfPlanePrincipal() const;
```

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output in the element. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::ELEMENT_FACE, specifying the results obtained for surface variables such as cavity radiation that are defined for the surface facets of an element.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*precision*

An odb_Enum::odb_PrecisionEnum specifying the precision of the output in the element. Possible values are:
- odb_Enum::SINGLE_PRECISION, specifying that the output values are in single precision.
- odb_Enum::DOUBLE_PRECISION, specifying that the output values are in double precision.

*elementLabel*

An Int specifying the element label of the element containing the location. *elementLabel* is available only if *position*=odb_Enum::INTEGRATION_POINT, odb_Enum::CENTROID, odb_Enum::ELEMENT_NODAL, or odb_Enum::ELEMENT_FACE.

*nodeLabel*

An Int specifying the node label of the node containing the location. *nodelabel* is available only if *position*=odb_Enum::ELEMENT_NODAL or odb_Enum::NODAL.

*integrationPoint*

An Int specifying the integration point in the element. *integrationPoint* is available only if *position*=odb_Enum::INTEGRATION_POINT.

*face*

An odb_Enum::odb_ElementFaceEnum specifying the face of the element. *face* is available only if *position*=odb_Enum::ELEMENT_FACE.

*type*

An odb_Enum::odb_DataTypeEnum specifying the output type. Possible values are odb_Enum::SCALAR, odb_Enum::VECTOR, odb_Enum::TENSOR_3D_FULL, odb_Enum::TENSOR_3D_PLANAR, odb_Enum::TENSOR_3D_SURFACE, odb_Enum::TENSOR_2D_PLANAR, and odb_Enum::TENSOR_2D_SURFACE.

*magnitude*

A Float specifying the length or magnitude of the vector. *magnitude* is valid only when *type*=odb_Enum::VECTOR.

*mises*

A Float specifying the calculated von Mises stress. The value is valid only when the *validInvariants* member includes odb_Enum::MISES; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*tresca*

A Float specifying the calculated Tresca stress. The value is valid only when the *validInvariants* member includes odb_Enum::TRESCA; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*press*

A Float specifying the calculated pressure stress. The value is valid only when the *validInvariants* member includes odb_Enum::PRESS; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*inv3*

A Float specifying the calculated third stress invariant. The value is valid only when the *validInvariants* member includes odb_Enum::INV3; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*maxPrincipal*

A Float specifying the calculated maximum principal stress. The value is valid only when the *validInvariants* member includes odb_Enum::MAX_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*midPrincipal*

A Float specifying the calculated intermediate principal stress. The value is valid only when the *validInvariants* member includes odb_Enum::MID_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*minPrincipal*

A Float specifying the minimum principal stress. The value is valid only when the *validInvariants* member includes odb_Enum::MIN_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*maxInPlanePrincipal*

A Float specifying the maximum principal in-plane stress. The value is valid only when the *validInvariants* member includes odb_Enum::MAX_INPLANE_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*minInPlanePrincipal*

A Float specifying the calculated minimum principal in-plane stress. The value is valid only when the *validInvariants* member includes odb_Enum::MIN_INPLANE_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*outOfPlanePrincipal*

A Float specifying the calculated principal out-of-plane stress. The value is valid only when the *validInvariants* member includes odb_Enum::OUTOFPLANE_PRINCIPAL; otherwise, the value is indeterminate. Conjugate data will be ignored in invariant calculation.

*instance*

An [OdbInstance](pt02ch61pyo16.md) object specifying the part to which the labels belong.

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md) object.

*localCoordSystem*

An odb_SequenceSequenceFloat specifying the 3 x 3 matrix of Floats specifying the direction cosines of the local coordinate system. Each sequence represents a row in the direction cosine matrix. *localCoordSystem* is available only for odb_Enum::TENSOR data written in a local coordinate system. If the underlying data are in double precision, an exception will be thrown.

*localCoordSystemDouble*

An odb_SequenceSequenceDouble specifying the 3 x 3 matrix of Doubles specifying the direction cosines of the local coordinate system. Each sequence represents a row in the direction cosine matrix. *localCoordSystemDouble* is available only for odb_Enum::TENSOR data written in a local coordinate system. If the underlying data are in single precision, an exception will be thrown.

*data*

A pointer to an array of Floats specifying data in the form described by *type*. If *type*=odb_Enum::TENSOR or odb_Enum::VECTOR, *data* is a sequence containing the components.  If the underlying data are in double precision an exception will be thrown.

*dataDouble*

A pointer to an array of Doubles specifying data in the form described by *type*. If *type*=odb_Enum::TENSOR or odb_Enum::VECTOR, *data* is a sequence containing the components.  If the underlying data are in single precision, an exception will be thrown.

*conjugateData*

A pointer to an array of Floats specifying data in the form described by *type*. If *type*=odb_Enum::TENSOR or odb_Enum::VECTOR, *conjugateData* is a sequence containing the components.  If the underlying data are in double precision, an exception will be thrown.

*conjugateDataDouble*

A pointer to an array of Doubles specifying data in the form described by *type*. If *type*=odb_Enum::TENSOR or odb_Enum::VECTOR, *conjugateData* is a sequence containing the components.  If the underlying data are in single precision, an exception will be thrown.




