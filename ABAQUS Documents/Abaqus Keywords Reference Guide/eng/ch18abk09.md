# *SFLOW







### *SFLOWDefine seepage coefficients and associated sink pore pressures normal to a surface.

This option is used to provide seepage coefficients and sink pore pressures to control pore fluid flow normal to the surface in consolidation analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Pore fluid flow," Section 34.4.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pporousflow)
- ["FLOW," Section 1.1.7 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uflow)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that gives the variation of reference pore pressure with time. If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). The AMPLITUDE parameter is ignored for nonuniform seepage flow boundary conditions defined in user subroutine [`FLOW`](../sub/sub-link.md#sub-xsl-flow) and for drainage-only seepage boundary conditions. 

OP

Set OP=MOD (default) to modify existing flows or to define additional flows.

Set OP=NEW if all existing [*SFLOW](ch18abk09.md)s applied to the model should be removed. New flows can be defined.

### **Data lines to define uniform seepage: **

**First line:**

Repeat this data line as often as necessary to define uniform seepage for various surfaces.

### **Data lines to define drainage-only seepage: **

**First line:**

Repeat this data line as often as necessary to define drainage-only seepage for various surfaces.

### **Data lines to define nonuniform seepage: **

**First line:**

The reference pore pressure value, ![](../graphics/key_eqn00712.gif), and reference seepage coefficient, ![](../graphics/key_eqn00556.gif), are defined in user subroutine [`FLOW`](../sub/sub-link.md#sub-xsl-flow) for nonuniform flow.

Repeat this data line as often as necessary to define nonuniform seepage for various surfaces.




