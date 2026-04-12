# 21.2 AnalyticalField object







The AnalyticalField object is the abstract base type for other AnalyticalField objects. The AnalyticalField object has no explicit constructor. The methods and members of the AnalyticalField object are common to all objects derived from the AnalyticalField.

The AnalyticalField object is derived from the [Field](pt01ch21pyo01.md) object.

**Access**

```
import fields
mdb.models[*name*].analyticalFields[*name*]
```

### 21.2.1 Members

The AnalyticalField object can have the following members:

*name*

A String specifying the repository key.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the field. If *localCsys*=`None`, the field is defined in the global coordinate system. The default value is `None`.

*description*

A String specifying the description of the field. The default value is an empty string.




