# 12.7 Principal stresses with bounding values for output field filtering







**Product: **Abaqus/Explicit  

**Benefits: **You can now apply a filter with a bounding value for maximum, intermediate, or minimum principal stress field output.

**Description: **When applying field filtering to the output, each component of a tensor or vector quantity is filtered individually and the maximum, minimum, or absolute maximum value and the limiting values are reported separately for each component.You can, however, apply a filter directly to an invariant. Three new values for the invariant parameter on field filtering are introduced: MAXP representing the maximum principal stress, INTERMP representing the intermediate principal stress, and MINP representing the minimum principal stress.
**References: **

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)

**Abaqus Keywords Reference Guide**
- [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput)
- [*FILTER](../key/key-link.md#usb-kws-mfilter)




