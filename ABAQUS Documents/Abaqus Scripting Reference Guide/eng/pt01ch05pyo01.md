# 5.1 Annotation object







The Annotation               object is the abstract base type for other Annotation               objects. The Annotation               object has no explicit constructor. The methods and members of the Annotation               object are common to all objects derived from Annotation.

**Access**

```
import annotationToolset
mdb.annotations[*name*]
session.odbs[*name*].userData.annotations[*name*]
session.viewports[*name*].annotationsToPlot[*i*]
```

### 5.1.1 bringToFront()

This method brings the Annotation                     object to the top of the annotation stack.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.2 sendToBack()

This method sends the Annotation                     object to the bottom of the annotation stack.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.3 bringForward()

This method brings the Annotation                     object one position up in the annotation stack.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.4 sendBackward()

This method sends the Annotation                     object one position down in the annotation stack.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.5 moveBefore(...)

This method moves the Annotation                     object before another object in the same repository.

**Required argument**

*name*

A String specifying the name of the other Annotation                              object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.6 moveAfter(...)

This method moves the Annotation                     object after another object in the same repository.

**Required argument**

*name*

A String specifying the name of the other Annotation                              object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.1.7 translate(...)

This method translates the Annotation                     object on the viewport plane.

**Required arguments**

None.

**Optional arguments**

*x*

A  Float specifying the *X*                                translation amount in millimeters.

*y*

A  Float specifying the *Y*                              translation amount in millimeters.

**Return value**

None

**Exceptions**

None.

### 5.1.8 Members

The Annotation object has the following member:

*name*

A String specifying the annotation repository key.




