# 61.30 UserData object







The UserData object contains user-defined XY data. The UserData object has no constructor; it is created automatically when an [Odb](pt02ch61pyo01.md) object is created. 

**Access**

```
odb.userData()
```

### 61.30.1 XYData(...)

This method creates an [XYData](#ker-xydata-cpp) object from a sequence of *X–Y* data pairs.

**Path**

```
odb.userData().XYData
```

**Prototype**

```
odb_UserData&
XYData(const odb_String& name,
       const odb_SequenceSequenceDouble& data,
       const odb_String& sourceDescription,
       const odb_String& contentDescription,
       const odb_String& positionDescription,
       const odb_String& legendLabel,
       const odb_String& xValuesLabel,
       const odb_String& yValuesLabel,
       const odb_QuantityType& axis1QuantityType,
       const odb_QuantityType& axis2QuantityType);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*data*

An odb_SequenceSequenceDouble specifying the *X–Y* data pairs.

**Optional arguments**

*sourceDescription*

An odb_String specifying the source of the *X–Y* data (e.g., “Entered from keyboard”, “Taken from ASCII file”, “Read from an ODB”, etc.). The default value is an empty string.

*contentDescription*

An odb_String specifying the content of the *X–Y* data (e.g., “field 1 vs. field 2”). The default value is an empty string.

*positionDescription*

An odb_String specifying additional information about the *X–Y* data (e.g., “for whole model”). The default value is an empty string.

*legendLabel*

An odb_String specifying the label to be used in the legend. The default value is the name of the XYData object.

*xValuesLabel*

An odb_String specifying the label for the X-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*yValuesLabel*

An odb_String specifying the label for the Y-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*axis1QuantityType*

A [QuantityType](#ker-quantitytype-cpp) object specifying the [QuantityType](#ker-quantitytype-cpp) object associated to the X -axis1- values.

*axis2QuantityType*

A [QuantityType](#ker-quantitytype-cpp) object specifying the [QuantityType](#ker-quantitytype-cpp) object associated to the Y -axis2- values.

**Return value**

An [XYData](#ker-xydata-cpp) object.

**Exceptions**

InvalidNameError.

### 61.30.2 Members

The UserData object can have the following members:

**Prototype**

```
odb_UserXYDataRepository& xyDataObjects();
odb_UserXYData& xyDataObjects(const odb_String& xyName);

```

*name*

An odb_String specifying the repository key.

*sourceDescription*

An odb_String specifying the source of the *X–Y* data (e.g., “Entered from keyboard”, “Taken from ASCII file”, “Read from an ODB”, etc.). The default value is an empty string.

*contentDescription*

An odb_String specifying the content of the *X–Y* data (e.g., “field 1 vs. field 2”). The default value is an empty string.

*positionDescription*

An odb_String specifying additional information about the *X–Y* data (e.g., “for whole model”). The default value is an empty string.

*xValuesLabel*

An odb_String specifying the label for the X-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*yValuesLabel*

An odb_String specifying the label for the Y-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*axis1QuantityType*

A [QuantityType](#ker-quantitytype-cpp) object specifying the [QuantityType](#ker-quantitytype-cpp) object associated to the X -axis1- values.

*axis2QuantityType*

A [QuantityType](#ker-quantitytype-cpp) object specifying the [QuantityType](#ker-quantitytype-cpp) object associated to the Y -axis2- values.

*legendLabel*

An odb_String specifying the label to be used in the legend. The default value is the name of the XYData object.

*xyDataObjects*

A repository of [UserXYData](pt02ch61pyo31.md) objects.

*data*

An odb_SequenceSequenceDouble specifying the *X–Y* data pairs.




