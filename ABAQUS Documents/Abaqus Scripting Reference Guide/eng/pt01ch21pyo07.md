# 21.7 OdbMeshRegionData object







The OdbMeshRegionData object defines the external source data of [MappedField](pt01ch21pyo06.md) from an ODB file.

**Access**

```
import field
mdb.models[*name*].analyticalFields[*name*].odbMeshRegionData
```

### 21.7.1 OdbMeshRegionData(...)

This method creates an OdbMeshRegionData object.

**Path**

```
mdb.models[*name*].analyticalFields[*name*].OdbMeshRegionData
```

**Required arguments**

*odbFileName*

A String specifying the name of the output database file (including the .odb extension) to be read into as the source data.                    This String can also be the full path to the output database file if it is located in another directory.

*variableLabel*

A String specifying the field output variable.

**Optional arguments**

*stepIndex*

An Int specifying the step index. Possible values are 0 ![](../graphics/ker_eqn00013.gif) *stepIndex* ![](../graphics/ker_eqn00013.gif) (*numSteps * 1). The default value is 0.

*frameIndex*

An Int specifying the frame in the specified step. Valid values are 0 ![](../graphics/ker_eqn00013.gif) *frameIndex* ![](../graphics/ker_eqn00013.gif) (*numFramesInStep * 1). The default value is 0.

*outputPosition*

A SymbolicConstant specifying the position from which to obtain data.                 Data can be obtained only from the position at which they were written to the output database during the analysis.                 This position should be aligned with the field output variable. Possible values are:
- UNDEFINED_POSITION
- NODAL
- INTEGRATION_POINT
- ELEMENT_FACE
- ELEMENT_NODAL
- ELEMENT_CENTROID
- WHOLE_ELEMENT
- WHOLE_REGION
- WHOLE_PART_INSTANCE
- WHOLE_MODEL
- GENERAL_PARTICLE

The default value is UNDEFINED_POSITION.

*dataType*

A SymbolicConstant specifying the data type of the field output variable which should be aligned with the variable.                 Currently only SCALAR is supported. Possible values are:
- ENUMERATION
- BOOLEAN
- INTEGER
- SCALAR
- VECTOR
- QUATERNION_2D
- QUATERNION_3D
- TENSOR
- TENSOR_3D_FULL
- TENSOR_3D_PLANAR
- TENSOR_3D_SURFACE
- TENSOR_2D_PLANAR
- TENSOR_2D_SURFACE

The default value is SCALAR.

*storageType*

A SymbolicConstant specifying the storage type of the field output variable which should be aligned with the variable. Possible values are FLOAT, DOUBLE, INTEGER, and BOOLEAN. The default value is FLOAT.

*quantityToPlot*

A SymbolicConstant specifying the quantity to plot. Currently only FIELD_OUTPUT is supported. Possible values are FIELD_OUTPUT and DISCONTINUITIES. The default value is FIELD_OUTPUT.

*averageElementOutput*

A Boolean specifying whether to average the element output. The default value is OFF.

*useRegionBoundaries*

A Boolean specifying whether to use region boundaries when averaging. The default value is OFF.

*regionBoundaries*

A SymbolicConstant specifying the type of averaging region boundaries. Currently only NONE and ODB_REGIONS are supported. Possible values are NONE, ODB_REGIONS, ELEMENT_SET, and DISPLAY_GROUPS. The default value is NONE.

*includeFeatureBoundaries*

A Boolean specifying whether to include additional averaging boundaries for shells and membranes based on feature edges. The default value is ON.

*featureAngle*

A Float specifying the feature angle to be used when *includeFeatureBoundaries*=ON. The default value is 20.0.

*averageOnlyDisplayed*

A Boolean specifying whether to average only values on displayed elements. The default value is OFF.

*averagingThreshold*

A Float specifying the nodal averaging threshold percentage.  0 ![](../graphics/ker_eqn00013.gif) *averagingThreshold* ![](../graphics/ker_eqn00013.gif)100. The default value is 75.0.

*computeOrder*

A SymbolicConstant specifying the order or the computations to be performed on the interested field output variable. Possible values are EXTRAPOLATE_AVERAGE_COMPUTE, EXTRAPOLATE_COMPUTE_AVERAGE, EXTRAPOLATE_COMPUTE, EXTRAPOLATE_COMPUTE_DISCONTINUITIES, and RAW_DATA. The default value is EXTRAPOLATE_COMPUTE_AVERAGE.

*numericForm*

A SymbolicConstant specifying the numeric form in which to display results that contain complex numbers. Possible values are COMPLEX_MAGNITUDE, COMPLEX_PHASE, REAL, IMAGINARY, and COMPLEX_MAG_AT_ANGLE. The default value is REAL.

*complexAngle*

A Float specifying the angle (in degrees) at which to display results that contain complex numbers when *numericForm=COMPLEX_MAG_AT_ANGLE*=COMPLEX_MAG_AT_ANGLE. The default value is 0.0.

**Return value**

An OdbMeshRegionData object.

**Exceptions**

TextException.

### 21.7.2 setValues(...)

This method modifies the OdbMeshRegionData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [OdbMeshRegionData](pt01ch21pyo07.md#ker-odbmeshregiondata-odbmeshregiondata-pyc) method.

**Return value**

None

**Exceptions**

### 21.7.3 Members

The OdbMeshRegionData object has the following members:

*stepIndex*

An Int specifying the step index. Possible values are 0 ![](../graphics/ker_eqn00013.gif) *stepIndex* ![](../graphics/ker_eqn00013.gif) (*numSteps * 1). The default value is 0.

*frameIndex*

An Int specifying the frame in the specified step. Valid values are 0 ![](../graphics/ker_eqn00013.gif) *frameIndex* ![](../graphics/ker_eqn00013.gif) (*numFramesInStep * 1). The default value is 0.

*outputPosition*

A SymbolicConstant specifying the position from which to obtain data.                 Data can be obtained only from the position at which they were written to the output database during the analysis.                 This position should be aligned with the field output variable. Possible values are:
- UNDEFINED_POSITION
- NODAL
- INTEGRATION_POINT
- ELEMENT_FACE
- ELEMENT_NODAL
- ELEMENT_CENTROID
- WHOLE_ELEMENT
- WHOLE_REGION
- WHOLE_PART_INSTANCE
- WHOLE_MODEL
- GENERAL_PARTICLE

The default value is UNDEFINED_POSITION.

*dataType*

A SymbolicConstant specifying the data type of the field output variable which should be aligned with the variable.                 Currently only SCALAR is supported. Possible values are:
- ENUMERATION
- BOOLEAN
- INTEGER
- SCALAR
- VECTOR
- QUATERNION_2D
- QUATERNION_3D
- TENSOR
- TENSOR_3D_FULL
- TENSOR_3D_PLANAR
- TENSOR_3D_SURFACE
- TENSOR_2D_PLANAR
- TENSOR_2D_SURFACE

The default value is SCALAR.

*storageType*

A SymbolicConstant specifying the storage type of the field output variable which should be aligned with the variable. Possible values are FLOAT, DOUBLE, INTEGER, and BOOLEAN. The default value is FLOAT.

*quantityToPlot*

A SymbolicConstant specifying the quantity to plot. Currently only FIELD_OUTPUT is supported. Possible values are FIELD_OUTPUT and DISCONTINUITIES. The default value is FIELD_OUTPUT.

*averageElementOutput*

A Boolean specifying whether to average the element output. The default value is OFF.

*useRegionBoundaries*

A Boolean specifying whether to use region boundaries when averaging. The default value is OFF.

*regionBoundaries*

A SymbolicConstant specifying the type of averaging region boundaries. Currently only NONE and ODB_REGIONS are supported. Possible values are NONE, ODB_REGIONS, ELEMENT_SET, and DISPLAY_GROUPS. The default value is NONE.

*includeFeatureBoundaries*

A Boolean specifying whether to include additional averaging boundaries for shells and membranes based on feature edges. The default value is ON.

*featureAngle*

A Float specifying the feature angle to be used when *includeFeatureBoundaries*=ON. The default value is 20.0.

*averageOnlyDisplayed*

A Boolean specifying whether to average only values on displayed elements. The default value is OFF.

*averagingThreshold*

A Float specifying the nodal averaging threshold percentage.  0 ![](../graphics/ker_eqn00013.gif) *averagingThreshold* ![](../graphics/ker_eqn00013.gif)100. The default value is 75.0.

*computeOrder*

A SymbolicConstant specifying the order or the computations to be performed on the interested field output variable. Possible values are EXTRAPOLATE_AVERAGE_COMPUTE, EXTRAPOLATE_COMPUTE_AVERAGE, EXTRAPOLATE_COMPUTE, EXTRAPOLATE_COMPUTE_DISCONTINUITIES, and RAW_DATA. The default value is EXTRAPOLATE_COMPUTE_AVERAGE.

*numericForm*

A SymbolicConstant specifying the numeric form in which to display results that contain complex numbers. Possible values are COMPLEX_MAGNITUDE, COMPLEX_PHASE, REAL, IMAGINARY, and COMPLEX_MAG_AT_ANGLE. The default value is REAL.

*complexAngle*

A Float specifying the angle (in degrees) at which to display results that contain complex numbers when *numericForm=COMPLEX_MAG_AT_ANGLE*=COMPLEX_MAG_AT_ANGLE. The default value is 0.0.

*odbFileName*

A String specifying the name of the output database file (including the .odb extension) to be read into as the source data.                    This String can also be the full path to the output database file if it is located in another directory.

*variableLabel*

A String specifying the field output variable.




