# *FILM







### *FILMDefine film coefficients and associated sink temperatures.

This option is used to provide film coefficients and sink temperatures for fully coupled thermal-stress analysis. In Abaqus/Standard it is also used to provide film coefficients and sink temperatures for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

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

If this parameter is omitted in an Abaqus/Standard analysis, the reference sink temperature is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference sink temperature is applied immediately at the beginning of the step. 

For nonuniform film coefficients (which are available only in Abaqus/Standard), the sink temperature amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film), and AMPLITUDE references are used only to modify the sink temperature passed into the user subroutine.

FILM AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the film coefficient, *h*, with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference film coefficient is applied immediately at the beginning of the step and kept constant over the step, independent of the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. If this parameter is omitted in an Abaqus/Explicit analysis, the reference film coefficient is applied immediately at the beginning of the step.

The FILM AMPLITUDE parameter is ignored if a film coefficient is defined to be a function of temperature and field variables via the [*FILM PROPERTY](ch06abk11.md) option.

For nonuniform film coefficients (which are available only in Abaqus/Standard), the film coefficient amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film), and FILM AMPLITUDE references are used only to modify the film coefficient passed into the user subroutine.

OP

Set OP=MOD (default) for existing [*FILM](ch06abk10.md)s to remain, with this option modifying existing films or defining additional films.

Set OP=NEW if all existing [*FILM](ch06abk10.md)s applied to the model should be removed.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for film conditions applied to the boundary of an adaptive mesh domain. If a film condition is applied to a surface in the interior of an adaptive mesh domain, the nodes on the surface will move with the material in all directions (they will be nonadaptive). Abaqus/Explicit will create a boundary region automatically on the surface subjected to the defined film load.

Set REGION TYPE=LAGRANGIAN (default) to apply the film condition to a Lagrangian boundary region. The edge of a Lagrangian boundary region will follow the material while allowing adaptive meshing along the edge and within the interior of the region.

Set REGION TYPE=SLIDING to apply the film condition to a sliding boundary region. The edge of a sliding boundary region will slide over the material. Adaptive meshing will occur along the edge and in the interior of the region. Mesh constraints are typically applied on the edge of a sliding boundary region to fix it spatially.

Set REGION TYPE=EULERIAN to apply the film condition to an Eulerian boundary region. This option is used to create a boundary region across which material can flow. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

### **Data lines to define sink temperatures and film coefficients: **

**First line:**

Repeat this data line as often as necessary to define film conditions.




