# *CFILM







### *CFILMDefine film coefficients and associated sink temperatures at one or more nodes or vertices.

This option is used to provide film coefficients and sink temperatures at any node in the model for fully coupled thermal-stress analysis. In Abaqus/Standard it is also used to provide film coefficients and sink temperatures at any node in the model for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["FILM," Section 1.1.6 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ufilm)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the sink temperature, ![](../graphics/key_eqn00086.gif), with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference sink temperature is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference sink temperature given on the data lines is applied immediately at the beginning of the step.

For nonuniform film coefficients (which are available only in Abaqus/Standard), the sink temperature amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film) and AMPLITUDE references are used only to modify the sink temperature passed into the user subroutine.

FILM AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the film coefficient, *h*, with time.

If this parameter is omitted, the reference film coefficient is applied immediately at the beginning of the step and kept constant over the step.

The FILM AMPLITUDE parameter is ignored if a film coefficient is defined to be a function of temperature and field variables via the [*FILM PROPERTY](ch06abk11.md) option.

For nonuniform film coefficients (which are available only in Abaqus/Standard), the film coefficient amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film) and FILM AMPLITUDE references are used only to modify the film coefficient passed into the user subroutine.

OP

Set OP=MOD (default) for existing [*CFILM](ch03abk14.md)s to remain, with this option modifying existing films or defining additional films.

Set OP=NEW if all existing [*CFILM](ch03abk14.md)s applied to the model should be removed.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for concentrated films applied on the boundary of an adaptive mesh domain. If concentrated films are applied to nodes in the interior of an adaptive mesh domain, these nodes will always follow the material.

Set REGION TYPE=LAGRANGIAN (default) to apply a concentrated film to a node that follows the material (nonadaptive).

Set REGION TYPE=SLIDING to apply a concentrated film to a node that can slide over the material. Mesh constraints are typically applied to the node to fix it spatially.

Set REGION TYPE=EULERIAN to apply a concentrated film to a node that can move independently of the material. This option is used only for boundary regions where the material can flow into or out of the adaptive mesh domain. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

USER

This parameter applies only to Abaqus/Standard analyses.

 Include this parameter to indicate that any nonzero film coefficients prescribed through this option will be defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film). If this parameter is used, any film coefficient and sink temperature values defined by the data lines of the option (and possibly modified by the AMPLITUDE and FILM AMPLITUDE parameters) are ignored and can be redefined in subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film).

### **Data lines to define sink temperatures and film coefficients: **

**First line:**

Repeat this data line as often as necessary to define film conditions.




