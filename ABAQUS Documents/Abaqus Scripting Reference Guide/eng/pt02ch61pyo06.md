# 61.6 FieldLocation object







The FieldLocation object specifies locations for which data are available in the field. For example, a displacement field will have a FieldLocation object with a *position* member value of NODAL. The FieldLocation object has no constructor; it is created automatically as an element of the *location* member of a [FieldOutput](pt02ch61pyo07.md) object by the `addData` method of a [FieldOutput](pt02ch61pyo07.md) object.

**Access**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].locations(*i*)
```

### 61.6.1 Members

The FieldLocation object can have the following members:

**Prototype**

```
odb_Enum::odb_ResultPositionEnum position() const;
const odb_SequenceSectionPoint& sectionPoints() const;
const odb_SectionPoint& sectionPoints(int index) const;
```

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the output in the element. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::ELEMENT_FACE.
- odb_Enum::CENTROID, specifying the value at the centroid obtained by extrapolating results calculated at the integration points.

*sectionPoints*

A sequence of [SectionPoint](pt02ch61pyo28.md) objects.




