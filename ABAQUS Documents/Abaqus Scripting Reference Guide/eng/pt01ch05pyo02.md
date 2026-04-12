# 5.2 AnnotationsToPlotArray object







The AnnotationsToPlotArray               object is a sequence that stores references to plotted annotations. By adding annotations to and removing annotations from this sequence, you can control which annotations are displayed in a particular viewport.

**Access**

```
import annotationToolset
session.viewports[*name*].annotationsToPlot
```

### 5.2.1 bringForward(...)

This method brings the [Annotation](pt01ch05pyo01.md)                     object one position forward in the AnnotationsToPlotArray                     sequence.

**Required argument**

*index*

An Int specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.2 bringToFront(...)

This method brings the [Annotation](pt01ch05pyo01.md)                     object to the beginning of the AnnotationsToPlotArray                     sequence.

**Required argument**

*index*

An Int specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.3 moveAfter(...)

This method moves the [Annotation](pt01ch05pyo01.md)                     object after another object in the same AnnotationsToPlotArray                     sequence.

**Required arguments**

*index*

An Integer specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

*other*

An Integer specifying the index of the other [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence after which this object will be moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.4 moveBefore(...)

This method moves the [Annotation](pt01ch05pyo01.md)                     object before another object in the same AnnotationsToPlotArray                     sequence.

**Required arguments**

*index*

An Int specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

*other*

An Int specifying the index of the other [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence before which this object will be moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.5 sendBackward(...)

This method sends the [Annotation](pt01ch05pyo01.md)                     object one position backward in the AnnotationsToPlotArray                     sequence.

**Required argument**

*index*

An Int specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.6 sendToBack(...)

This method sends the [Annotation](pt01ch05pyo01.md)                     object to the end of the AnnotationsToPlotArray                     sequence.

**Required argument**

*index*

An Int specifying the index of the [Annotation](pt01ch05pyo01.md)                              object in the AnnotationsToPlotArray                              sequence.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 5.2.7 Members

The AnnotationsToPlotArray object has no members.




