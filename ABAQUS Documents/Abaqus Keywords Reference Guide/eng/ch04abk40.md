# *DSFLOW







### *DSFLOWSpecify distributed seepage flows normal to a surface.

This option is used to input seepage flows (pore fluid velocities) normal to surfaces of the model in consolidation problems.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Pore fluid flow," Section 34.4.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pporousflow)
- ["DFLOW," Section 1.1.2 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udflow)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) curve that defines the magnitude of the seepage flow during the step. If this parameter is omitted for uniform seepage types, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). Amplitude references are ignored for flows defined in user subroutine [`DFLOW`](../sub/sub-link.md#sub-xsl-dflow).

OP

Set OP=MOD (default) for existing [*DSFLOW](ch04abk40.md)s to remain, with this option modifying existing flows or defining additional flows.

Set OP=NEW if all existing [*DSFLOW](ch04abk40.md)s applied to the model should be removed. New flows can be defined.

### **Data lines to define uniform seepage: **

**First line:**

Repeat this data line as often as necessary to define uniform seepage for various surfaces.

### **Data lines to define nonuniform seepage: **

**First line:**

Nonuniform seepage magnitudes are defined via user subroutine [`DFLOW`](../sub/sub-link.md#sub-xsl-dflow).

Repeat this data line as often as necessary to define nonuniform seepage for surfaces.




