# 5.4 Text object







The Text                 object stores the text settings and location of a text annotation.

The Text object is derived from the [Annotation](pt01ch05pyo01.md) object.

**Access**

```
import annotationToolset
mdb.annotations[*name*]
session.odbs[*name*].userData.annotations[*name*]
session.viewports[*name*].annotationsToPlot[*i*]
```

### 5.4.1 Text(...)

This method creates a Text                       object.

**Path**

```
mdb.Text
```

```
session.odbs[*name*].userData.Text
```

**Required argument**

*name*

A String specifying the annotation repository key.

**Optional arguments**

*text*

A String specifying the text of the Text                             object.                          The default value is an empty string.

*offset*

A pair of Floats specifying the *X*- and *Y*-offsets in millimeters of the Text                             object from *anchor*.                          The default value is (0, 0).

*anchor*

A SymbolicConstant or a sequence of Floats specifying a point. A sequence of two Floats specifies the *X*- and *Y* coordinates as percentages of the viewport width and height. A Sequence of three Floats specifies the *X*-,  *Y*-, and *Z*-coordinates of a point in the model coordinate system. A SymbolicConstant specifies a relative position.                          Possible values are:
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

The default value is BOTTOM_LEFT.

*referencePoint*

A SymbolicConstant or a sequence of Floats specifying a point. The sequence of two Floats specifies the *X*- and *Y*-coordinates of the reference point of the Text                             annotation given as percentages of its width and height. The SymbolicConstant indicates a relative position.                          Possible values are:
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

The default value is BOTTOM_LEFT.

*rotationAngle*

A Float specifying the amount of rotation in degrees about *referencePoint*.                       The default value is 0.0.

*color*

A String specifying the color of the Text                             object. Possible string values are any valid color.                          The default value is "White".

*font*

A String specifying the font of the Text                             object. Possible string values are any valid font specification.                          The default value is "-*-helvetica-medium-r-normal--12-*".

*backgroundStyle*

A SymbolicConstant specifying the Text                          object background style.                       Possible values are MATCH, TRANSPARENT, and OTHER. The default value is TRANSPARENT.

*backgroundColor*

A String specifying the color of the Text                             object background. Possible string values are any valid color. The default value matches the viewport background.

*box*

A Boolean specifying whether the box around the text is shown. The default value is OFF.

*justification*

A SymbolicConstant specifying the Text                          object justification for multiline text.                       Possible values are JUSTIFY_LEFT, JUSTIFY_CENTER, and JUSTIFY_RIGHT. The default value is JUSTIFY_LEFT.

**Return value**

A Text object.

**Exceptions**

None.

### 5.4.2 setValues(...)

This method modifies the Text object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Text](pt01ch05pyo04.md#ker-text-text-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 5.4.3 Members

The Text object has members with the same names and descriptions as the arguments to the [Text](pt01ch05pyo04.md#ker-text-text-pyc) method.

In addition, the Text object has the following members:

*width*

A Float specifying the width in millimeters of the Text                          object.

*height*

A Float specifying the height in millimeters of the Text                          object.




