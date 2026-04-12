# 2.10 Model object







The following commands operate on Model objects. For more information about the Model object, see ["Model object," Section 33.1](pt01ch33pyo01.md).

**Access**

```
import mesh
```

### 2.10.1 adaptiveRemesh(...)

This method remeshes the model using the active remesh rules in the model and the error indicator results from a previous analysis.

**Required argument**

*odb*

An [Odb](pt01ch34pyo01.md)                              object containing error output field results.

**Optional arguments**

None.

**Return value**

An [AdaptivityIteration](pt01ch02pyo05.md)                     Object.

**Exceptions**

None.



