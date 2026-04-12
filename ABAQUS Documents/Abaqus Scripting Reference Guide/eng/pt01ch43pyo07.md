# 43.7 TiffOptions object







The TiffOptions object stores the settings that Abaqus uses when printing in TIFF               format. The TiffOptions               object has no constructor. Abaqus creates the *tiffOptions*               member when a session is started.

**Access**

```
session.tiffOptions
```

### 43.7.1 setValues(...)

This method modifies the TiffOptions                     object.

**Required arguments**

None.

**Optional argument**

*imageSize*

The SymbolicConstant SIZE_ON_SCREEN or a pair of Ints specifying the width and height of the image in pixels. Possible values are (*minWidth*, *minHeight*) ![](../graphics/ker_eqn00013.gif)                      *imageSize*                      ![](../graphics/ker_eqn00013.gif)                       (*maxWidth*                     and *maxHeight*).                    The default value is SIZE_ON_SCREEN.

**Note:**The minimum value of width and height (*minWidth*                           and *minHeight*                           ) is the number of pixels that occupy 10 mm at the current screen resolution. The value is typically around 50 pixels and may be different for width and height.

The maximum value of width and height (*maxWidth*                           and *maxHeight*                           ) is the largest number of pixels supported by the system graphics and will be at least as large as the screen dimensions.

**Return value**

None

**Exceptions**

RangeError.

If either the width or height arguments of *imageSize*                           are out of range (where *minWidth*                           and *minHeight*                           are the number of pixels corresponding to approximately 10 mm for a given display and *maxWidth*                           and *maxHeight*                           are the largest allowable number of pixels supported by the system graphics):

```
RangeError: imageSize must be SIZE_ON_SCREEN or a sequence of 2 Ints in the range (minWidth, minHeight) <= (width, height) <= (maxWidth, maxHeight).                         
```

### 43.7.2 Members

The TiffOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch43pyo07.md#ker-tiffoptions-setvalues-pyc) method.




