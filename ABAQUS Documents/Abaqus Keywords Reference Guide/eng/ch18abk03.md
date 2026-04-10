# *SECTION ORIGIN







### *SECTION ORIGINDefine a meshed cross-section origin.

This option is used in conjunction with the [*BEAM SECTION GENERATE](ch02abk07.md) option to define the location of the beam node on a meshed beam cross-section.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Meshed beam cross-sections," Section 10.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ameshedsection)
- [*BEAM SECTION GENERATE](ch02abk07.md)

### **Optional parameter: **

ORIGIN

Set ORIGIN=CENTROID to place the beam node at the section centroid.

Set ORIGIN=SHEAR CENTER to place the beam node at the shear center.

### **Data line to define the location of the beam node if the ORIGIN parameter is omitted: **

**First (and only) data line:**

If this option is not used, the section origin is placed at the origin of the coordinate system on the meshed cross-section model. If this option is used without the ORIGIN parameter and no data line is given, the section origin is placed at the centroid.




