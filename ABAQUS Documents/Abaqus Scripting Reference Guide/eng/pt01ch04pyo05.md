# 4.5 ImageAnimation object







The ImageAnimation object is used to build frame by frame animation.

**Access**

```
import animation
session.imageAnimation
```

### 4.5.1 ImageAnimation(...)

This method creates an ImageAnimation object from the specified filename and format.

**Path**

```
session.ImageAnimation
```

**Required arguments**

*fileName*

A String specifying the name of the animation file to generate.

*format*

A SymbolicConstant specifying the format of the generated file. Possible values are AVI, QUICKTIME.

**Optional arguments**

None.

**Return value**

An ImageAnimation object.

**Exceptions**

None.

### 4.5.2 writeFrame(...)

This method adds a frame to the ImageAnimation object.

**Required arguments**

None.

**Optional argument**

*canvasObjects*

A sequence specifying the canvas objects to capture. The default is to capture all canvas objects.

**Return value**

None

**Exceptions**

None.

### 4.5.3 close()

This method closes the ImageAnimation object.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.5.4 closed()

This method indicates if the ImageAnimation is open or closed for writing animation frames.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.5.5 Members

The ImageAnimation object has the following member:

*fileName*

A String specifying the file to which the animation frames is to be written.




