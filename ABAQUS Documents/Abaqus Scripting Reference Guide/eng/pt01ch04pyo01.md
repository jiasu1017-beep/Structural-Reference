# 4.1 AnimationController object







The AnimationController object controls all object-based animation to be displayed in the viewports. The AnimationController object has no constructor. Abaqus creates the *animationController* member when it creates the [Session](pt01ch47pyo01.md) object.

**Access**

```
import animation
session.animationController
```

### 4.1.1 play(...)

This method begins the animation.

**Required arguments**

None.

**Optional argument**

*duration*

The SymbolicConstant UNLIMITED or an Int specifying how many seconds to play the animation. The default value is UNLIMITED.

**Return value**

None

**Exceptions**

If *animationType*=NONE:

```
AnimationError: animationType not set
```

### 4.1.2 stop()

This method stops the animation.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.1.3 incrementFrame()

This method increments the animation frame.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.1.4 decrementFrame()

This method decrements the animation frame.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.1.5 showFrame(...)

This method renders the specified frame of the animation.

**Required arguments**

None.

**Optional arguments**

*frame*

An Int specifying the frame number.

*value*

A Float specifying the frame: for *animationType*=TIME_HISTORY the frame with the time nearest to this value, for *animationType*=HARMONIC the frame with the angle nearest to this value,  for *animationType*=SCALE_FACTOR the frame with the scale value nearest to this value.

**Return value**

None

**Exceptions**

None.

### 4.1.6 showFirstFrame()

This method renders the first frame of the animation.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.1.7 showLastFrame()

This method renders the last frame of the animation.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 4.1.8 setValues(...)

This method modifies the AnimationController object.

**Required arguments**

None.

**Optional arguments**

*animationType*

A SymbolicConstant specifying the type of movie to play. Possible values are SCALE_FACTOR, HARMONIC, TIME_HISTORY, and NONE. The default value is NONE.

*viewports*

A sequence of pairs of Strings specifying the name of a viewport where the animation is active followed by a layer name, or the SymbolicConstant ALL. If a layer name is not supplied, the current layer is used. If the viewport is in single display mode, the layer name is ignored if it is specified. The default value is an empty sequence.

**Return value**

None

**Exceptions**

RangeError.

### 4.1.9 Members

The AnimationController object can have the following members:

*animationType*

A SymbolicConstant specifying the type of movie to play. Possible values are SCALE_FACTOR, HARMONIC, TIME_HISTORY, and NONE. The default value is NONE.

*state*

A SymbolicConstant specifying the state of the animation controller. Possible values are STOP and PLAY. The default value is STOP.

*animationOptions*

An [AnimationOptions](pt01ch04pyo02.md) object.

*viewports*

A tuple of pairs of Strings specifying the name of a viewport where the animation is active followed by a layer name, or the SymbolicConstant ALL. If a layer name is not supplied, the current layer is used. If the viewport is in single display mode, the layer name is ignored if it is specified. The default value is an empty sequence.




