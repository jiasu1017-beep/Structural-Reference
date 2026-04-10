# *RADIATE







### *RADIATESpecify radiation conditions in heat transfer analyses.

This option is used to apply radiation boundary conditions between a nonconcave surface and a nonreflecting environment in fully coupled thermal-stress analysis. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

It must be used in conjunction with the [*PHYSICAL CONSTANTS](ch16abk09.md) option, which is used to define the Stefan-Boltzmann constant.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the ambient temperature with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude given on the data lines is applied throughout the step.

OP

Set OP=MOD (default) for existing [*RADIATE](ch17abk01.md) definitions to remain, with this option modifying existing radiation conditions or defining additional radiation conditions. 

Set OP=NEW if all existing [*RADIATE](ch17abk01.md) definitions applied to the model should be removed.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for radiation conditions applied to the boundary of an adaptive mesh domain. If a radiation condition is applied to a surface in the interior of an adaptive mesh domain, the nodes on the surface will move with the material in all directions (they will be nonadaptive). Abaqus/Explicit will create a boundary region automatically on the surface subjected to the defined radiation condition.

Set REGION TYPE=LAGRANGIAN (default) to apply the radiation condition to a Lagrangian boundary region. The edge of a Lagrangian boundary region will follow the material while allowing adaptive meshing along the edge and within the interior of the region.

Set REGION TYPE=SLIDING to apply the radiation condition to a sliding boundary region. The edge of a sliding boundary region will slide over the material. Adaptive meshing will occur along the edge and in the interior of the region. Mesh constraints are typically applied on the edge of a sliding boundary region to fix it spatially.

Set REGION TYPE=EULERIAN to apply the radiation condition to an Eulerian boundary region. This option is used to create a boundary region across which material can flow. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

### **Data lines to define radiation conditions: **

**First line:**

Repeat this data line as often as necessary to define radiation conditions.




