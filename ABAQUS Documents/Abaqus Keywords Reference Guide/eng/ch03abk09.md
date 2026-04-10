# *CAVITY DEFINITION







### *CAVITY DEFINITIONDefine a cavity for thermal radiation.

This option is used to define cavities for thermal radiation heat transfer. It can be used only in conjunction with the [*SURFACE](ch18abk47.md), TYPE=ELEMENT option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- [*SURFACE](ch18abk47.md)
- [*SURFACE PROPERTY](ch18abk52.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the cavity.

### **Optional parameters: **

AMBIENT TEMP

Set this parameter equal to the reference temperature of the external medium to which radiation takes place in the case of an open cavity. If this parameter is omitted, the cavity is assumed to be closed.

PARALLEL DECOMPOSITION

Set PARALLEL DECOMPOSITION=ON to enable parallel decomposition of a cavity during a cavity radiation analysis.

Set PARALLEL DECOMPOSITION=OFF (default) to disable parallel decomposition of a cavity during a cavity radiation analysis.

SET PROPERTY

Include this parameter to set, or to redefine, surface properties for the surfaces making up the cavity. If this parameter is omitted, the cavity is assumed to consist of surfaces for which surface properties have already been defined as part of the surface definitions.

### **Data lines to define a cavity for thermal radiation using surfaces with defined surface properties (default): **

**First line:**

Repeat this data line as often as necessary to define the cavity. Up to 16 entries are allowed per line.

### **Data lines to define a cavity when the SET PROPERTY parameter is included: **

**First line:**

Repeat this data line as often as necessary to define the cavity.  Up to 16 entries are allowed per line.




