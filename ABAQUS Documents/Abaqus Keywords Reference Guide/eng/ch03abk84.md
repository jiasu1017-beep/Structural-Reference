# *CRADIATE







### *CRADIATESpecify radiation conditions and associated sink temperatures at one or more nodes or vertices.

This option is used to apply radiation boundary conditions between a node and a nonreflecting environment in fully coupled thermal-stress analysis. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the ambient temperature with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step.

OP

Set OP=MOD (default) for existing [*CRADIATE](ch03abk84.md) definitions to remain, with this option modifying existing radiation conditions or defining additional radiation conditions. 

Set OP=NEW if all existing [*CRADIATE](ch03abk84.md) definitions applied to the model should be removed.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for concentrated radiation conditions applied on the boundary of an adaptive mesh domain. If concentrated radiation conditions are applied to nodes in the interior of an adaptive mesh domain, these nodes will always follow the material.

Set REGION TYPE=LAGRANGIAN (default) to apply a concentrated radiation condition to a node that follows the material (nonadaptive).

Set REGION TYPE=SLIDING to apply a concentrated radiation condition to a node that can slide over the material. Mesh constraints are typically applied to the node to fix it spatially.

Set REGION TYPE=EULERIAN to apply a concentrated radiation condition to a node that can move independently of the material. This option is used only for boundary regions where the material can flow into or out of the adaptive mesh domain. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

### **Data lines to define radiation conditions: **

**First line:**

Repeat this data line as often as necessary to define radiation conditions.




