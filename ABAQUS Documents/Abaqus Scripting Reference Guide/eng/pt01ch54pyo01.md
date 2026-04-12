# 54.1 View object







The [Session](pt01ch47pyo01.md)               and [Viewport](pt01ch11pyo04.md) View               objects store view settings for custom (both predefined and user-defined) views. The paradigm used to define a view is based on a camera analogy.                     Similar to taking a photograph with a camera, features such as camera position, view direction, orientation, depth of field, and projection are specified to transform three-dimensional views to the screen.

The [Layer](pt01ch11pyo03.md) View               objects store a transformation matrix used to position the contents of the [Layer](pt01ch11pyo03.md)               within a viewport.

**Access**

```
session.viewports[*name*].layers[*name*].view
session.viewports[*name*].view
session.views[*name*]
```

### 54.1.1 View(...)

This method creates a View                     object.

**Note:**All dimensions and coordinates are specified in the model coordinate system.

**Note:**This method cannot be used to create a View                           for a [Layer](pt01ch11pyo03.md)                           object.

**Path**

```
session.View
```

**Required arguments**

*name*

A String specifying the name of the view (also used as the repository key). Possible values are 'Front', 'Back', 'Top', 'Bottom', 'Left', `Right', 'Iso', 'User-1', 'User-2', 'User-3', and 'User-4'. The object member associated with this argument is a SymbolicConstant. Possible values of the *name*                  member are:FRONT, BACK, TOP, BOTTOM, LEFT, RIGHT, ISO, USER1, USER2, USER3, and USER4.

*fieldOfViewAngle*

A Float specifying the viewing angle of the camera. Possible values are 0.0 ![](../graphics/ker_eqn00048.gif)                   *fieldOfViewAngle*                   ![](../graphics/ker_eqn00048.gif)                  180.0.

*nearPlane*

A Float specifying the distance from the camera to the near clipping plane. Possible values are *nearPlane*                   ![](../graphics/ker_eqn00060.gif)                  0.0.

*farPlaneMode*

A SymbolicConstant specifying how the distance from the camera to the far clipping plane is set. Possible values are AUTO_COMPUTE and SPECIFY.

*farPlane*

A Float specifying the distance from the camera to the far clipping plane when *farPlaneMode*                  =SPECIFY. Possible values are *farPlane*                   ![](../graphics/ker_eqn00060.gif)                   *nearPlane*.

*width*

A Float specifying the width of the front clipping plane. Possible values are *width*                   ![](../graphics/ker_eqn00060.gif)                  0.0.

*height*

A Float specifying the height of the front clipping plane. Possible values are *height*                   ![](../graphics/ker_eqn00060.gif)                  0.0.

*projection*

A SymbolicConstant specifying the projection mode. Possible values are PERSPECTIVE and PARALLEL.

*cameraPosition*

A sequence of three Floats specifying the camera position.

*cameraUpVector*

A sequence of three Floats specifying the camera's up vector (the screen's positive *Y*-axis). The initial value is (0, 0, 0).

*cameraTarget*

A sequence of three Floats specifying the center of the scene.

*viewOffsetX*

A Float specifying the amount to pan the model in the screen *X*-direction as a fraction of the viewport width. A positive value pans the model to the right. A negative value pans the model to the left.

The*viewOffsetX*                  and *viewOffsetY*                  arguments allow you to pan the view without changing the position of the camera or the target (*cameraPosition*                  and *cameraTarget*                  arguments to the `View`                  method). The resulting change in the view allows you to pan a perspective display without producing an apparent rotation of the model.

*viewOffsetY*

A Float specifying the amount to pan the model in the screen *Y*-direction as a fraction of the viewport height. A positive value pans the model upward. A negative value pans the model downward.

*autoFit*

A Boolean specifying whether the view is auto-fit when applied.

**Optional argument**

*movieMode*

A Boolean specifying whether or not the camera is in movie mode. The default value is OFF.

**Return value**

A View object.

**Exceptions**

RangeError.

### 54.1.2 fitView(...)

This method scales the displayable object (such as a part, the assembly, or an *X–Y* plot) to fit the viewport.

**Required arguments**

None.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This is typically only used when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.3 next(...)

This method restores the view in the viewport to the next view setting in the list. (There is a list of eight views stored for each viewport.) If there is no next view, no action is taken.

**Note:**This method is not available for a [Layer](pt01ch11pyo03.md) View.

**Required arguments**

None.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This is typically only used when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.4 pan(...)

This method pans the view in the viewport using absolute, not relative, mode.

**Required arguments**

None.

**Optional arguments**

*xFraction*

A Float specifying the amount to pan the model in the screen *X*-direction as a fraction of the viewport width. A positive value pans the model to the right. A negative value pans the model to the left. The default value is 0.0.

*yFraction*

A Float specifying the amount to pan the model in the screen *Y*-direction as a fraction of the viewport height. A positive value pans the model upward. A negative value pans the model downward. The default value is 0.0.

*asMovie*

A Boolean specifying the alternate mode of the `pan`                              view manipulation should be used. The default value is OFF. This argument is ignored for a [Layer](pt01ch11pyo03.md) View.

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.5 previous(...)

This method restores the view in the viewport to the previous view setting in the list. (There is a list of eight views stored for each viewport.) If there is no previous view, no action is taken. 

**Note:**This method is not available for a [Layer](pt01ch11pyo03.md) View.

**Required arguments**

None.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.6 rotate(...)

This method rotates the view in the viewport.  If a center of rotation has been previously specified and *asMovie*                     is OFF                     then this method will honor that rotation center.

**Required arguments**

None.

**Optional arguments**

*xAngle*

A Float specifying the degrees to rotate about the *X*-axis. The default value is 0.0.

*yAngle*

A Float specifying the degrees to rotate about the *Y*-axis. The default value is 0.0.

*zAngle*

                             A Float specifying the degrees to rotate about the*Z*-axis. The default value is 0.0.

*mode*

A SymbolicConstant specifying the rotation mode. Possible values are:
- TOTAL : Set the view to (0, 0, 1), then rotate about the screen's axes (an absolute rotation).
- SCREEN : Rotate incrementally about the screen's axes (a relative rotation).
- MODEL : Rotate incrementally about the model's axes (a relative rotation).

                              The default value is MODEL.

*asMovie*

A Boolean specifying the alternate mode of the `rotate`                              view manipulation should be used. The default value is OFF.

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.7 setLayerTransform(...)

This method modifies the transformation used to position a [Layer](pt01ch11pyo03.md).

**Note:**This method is not available for [Session](pt01ch47pyo01.md)                           and [Viewport](pt01ch11pyo04.md) Views.

**Required arguments**

None.

**Optional arguments**

*layerTransform*

A sequence of 16 Floats specifying the transformation matrix.

*options*

A View                              object from which the view settings are to be copied. If the *layerTransform*                              argument is also supplied to `setLayerTransform`, it will override the values in the View                              object specified by *view*.

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.8 setProjection(...)

This method modifies the appearance of three-dimensional models in the viewport. Choosing PERSPECTIVE                     makes a model appear more realistic by decreasing the apparent size of features that are farther away from the viewing point.

**Note:**This method is not available for a [Layer](pt01ch11pyo03.md) View.

**Required argument**

*projection*

A SymbolicConstant specifying the projection mode. Possible values are PERSPECTIVE and PARALLEL.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

RangeError.

### 54.1.9 setRotationCenter(...)

This method sets the center of rotation to the specified location.

**Required argument**

*rotationCenter*

A sequence of a String and an Int specifying a part instance name and a node label or a sequence of 3 Floats specifying a point.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TypeError: rotationCenter cannot be set using a part instance and node label unless the displayed object is an ODB

### 54.1.10 setValues(...)

This method modifies the View                     object.

**Note:**This method is not available for a [Layer](pt01ch11pyo03.md) View.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues`                        are the same as the arguments to the [View](pt01ch54pyo01.md#ker-view-view-pyc)                        method, except for the *name*                        and *autoFit*                        arguments. In addition, `setValues`                        has the following optional arguments:

*options*

A View                              object from which the view settings are to be copied. If other arguments are also supplied to `setValues`, they will override the values in the View                              object specified by *view*.

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

RangeError.

### 54.1.11 setViewpoint(...)

This method sets the camera's position in the viewport.

**Note:**This method is not available for a [Layer](pt01ch11pyo03.md) View.

**Required argument**

*viewVector*

A sequence of three Floats specifying the viewing vector (from the camera to the origin of the model).

**Optional arguments**

*cameraUpVector*

A sequence of three Floats specifying the camera's up vector (the screen's positive *Y*-axis). The initial value is (0, 0, 0).

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.12 zoom(...)

This method magnifies the view in the viewport.

**Required argument**

*zoomFactor*

A Float specifying the amount to zoom. Possible values are 0.000001 ![](../graphics/ker_eqn00013.gif)                               *zoomFactor*                               ![](../graphics/ker_eqn00013.gif)                              1000000. A *zoomFactor*                              less than one reduces the image. A *zoomFactor*                              greater than one enlarges the image.

**Optional arguments**

*mode*

A SymbolicConstant specifying the way the zoom is executed. Possible values are:
- ABSOLUTE : Execute `fitView`, then zoom.
- RELATIVE : Zoom from the current camera settings.

                              The default value is ABSOLUTE.

*asMovie*

A Boolean specifying the alternate mode of the `zoom`                              view manipulation should be used. The default value is OFF. This argument is ignored for a [Layer](pt01ch11pyo03.md) View.

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

RangeError.

### 54.1.13 zoomRectangle(...)

This method fills the viewport with the graphics located within the given rectangle.

**Required arguments**

*point1*

A pair of Floats specifying the*X*- and *Y*-coordinates of one corner of the rectangle in fractions of the viewport width and height.

*point2*

A pair of Floats specifying the*X*- and *Y*-coordinates of the other corner of the rectangle in fractions of the viewport width and height.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This argument is typically used only when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 54.1.14 Members

The View object has members with the same names and descriptions as the arguments to the [View](pt01ch54pyo01.md#ker-view-view-pyc) method.

In addition, the View object has the following members:

*displayedObjectScreenWidth*

A Float specifying the width in viewport millimeters of the bounding rectangle around the viewport contents. This value does not include annotations or symbols and it is not clipped to the size of the viewport window.

*displayedObjectScreenHeight*

A Float specifying the height in viewport millimeters of the bounding rectangle around the viewport contents. This value does not include annotations or symbols and it is not clipped to the size of the viewport window.

*layerTransform*

A tuple of Floats specifying a transformation matrix used to position the contents of the [Layer](pt01ch11pyo03.md)                     within a viewport.




