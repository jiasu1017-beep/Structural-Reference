# 61.31 UserXYData object







The UserXYData object stores a sequence of pairs and information about the axes.

**Access**

```
Api.userData().xyDataObjects()[*name*]
```

### 61.31.1 addData(...)

This method replaces the contents of the *data* member of the [XYData](#ker-xydata-cpp) object.

**Prototype**

```
void
addData(const odb_SequenceSequenceDouble& data);
```

**Required argument**

*data*

An odb_SequenceSequenceDouble specifying the *X–Y* data pairs.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.31.2 getData()

Returns the contents of the *data* member of the [XYData](#ker-xydata-cpp) object.

**Prototype**

```
odb_SequenceSequenceFloat
getData();
```

**Arguments**

None.

**Return value**

An odb_SequenceSequenceFloat.

**Exceptions**

None.

### 61.31.3 Members

The UserXYData object can have the following members:

**Prototype**

```
odb_String name() const;
odb_String sourceDescription() const;
odb_String contentDescription() const;
odb_String positionDescription() const;
odb_String xAxisLabel() const;
odb_String yAxisLabel() const;
odb_String legendLabel() const;
odb_String description() const;
odb_SequenceSequenceDouble data() const;
```

*name*

An odb_String specifying the repository key.

*sourceDescription*

An odb_String specifying the source of the *X–Y* data (e.g., “Entered from keyboard”, “Taken from ASCII file”, “Read from an ODB”, etc.). The default value is an empty string.

*contentDescription*

An odb_String specifying the content of the *X–Y* data (e.g., “field 1 vs. field 2”). The default value is an empty string.

*positionDescription*

An odb_String specifying additional information about the *X–Y* data (e.g., “for whole model”). The default value is an empty string.

*xAxisLabel*

An odb_String specifying the label for the X-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*yAxisLabel*

An odb_String specifying the label for the Y-values. This value may be overridden if the *X–Y* data are combined with other *X–Y* data.  The default value is an empty string.

*legendLabel*

An odb_String specifying the label to be used in the legend. The default value is the name of the XYData object.

*description*

An odb_String specifying the complete description of the XYData object.

*data*

An odb_SequenceSequenceDouble specifying the *X–Y* data pairs.




