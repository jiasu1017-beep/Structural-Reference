# *REBAR LAYER







### *REBAR LAYERDefine layers of reinforcement in membrane, shell, surface, and continuum elements.

This option is used to define one or multiple rebar layers in membrane, shell, and surface elements. It must be used in conjunction with the [*MEMBRANE SECTION](ch13abk16.md), the [*SHELL SECTION](ch18abk15.md), or the [*SURFACE SECTION](ch18abk54.md) option. Rebar layers in solid (continuum) elements can be defined by embedding a set of surface or membrane elements with rebar layers in a set of host continuum elements through the use of the [*EMBEDDED ELEMENT](ch05abk14.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module; supported only for membrane and shell elements.

##### **References:**

- ["Defining reinforcement," Section 2.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebarlayer)
- ["Embedded elements," Section 35.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pembeddedelement)
- [*EMBEDDED ELEMENT](ch05abk14.md)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL SECTION](ch18abk15.md)
- [*SURFACE SECTION](ch18abk54.md)

### **Optional parameters: **

 GEOMETRY

Use this parameter to specify the type of rebar geometry. 

Set GEOMETRY=CONSTANT (default) if the rebar spacing in the element is constant. The spacing is given as a length measure on the data lines.

Set GEOMETRY=ANGULAR if the rebar spacing increases linearly as a function of the distance measured from the axis of revolution in a cylindrical coordinate system. The spacing is given as an angular spacing in degrees on the data lines. A cylindrical orientation system must be defined if this option is used with three-dimensional membrane, shell, or surface elements. 

Set GEOMETRY=LIFT EQUATION if the rebar spacing and orientation within the element is determined by the tire “lift” equation. The rebar parameters are defined with respect to the uncured or “green” tire configuration, and the lift equation maps the rebar parameters to the cured tire configuration. The spacing is given as a length measure on the data lines. A cylindrical orientation system must be defined if this option is used with three-dimensional membrane, shell, or surface elements. 

ORIENTATION

This parameter is meaningful only for rebar in general shell, membrane, and surface elements. Set this parameter equal to the name of an orientation definition that defines the angular orientation of the rebar on the data lines. If this parameter is omitted, the angular orientation of rebar on the data lines is specified relative to the default projected local surface directions. This parameter is not permitted with axisymmetric shell, axisymmetric membrane, and axisymmetric surface elements. 

### **Data lines to define rebar layers: **

**First line:**

Repeat the data line as often as necessary. Each data line defines a layer of rebar.




