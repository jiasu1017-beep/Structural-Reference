# *CFLUX







### *CFLUXSpecify concentrated fluxes in heat transfer or mass diffusion analyses.

This option is used to apply a flux to any node of the model in fully coupled thermal-stress analysis. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, coupled thermal-electrical-structural, and mass diffusion analyses.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)

### **Required parameter for reading concentrated nodal flux from an output database file: **

FILE

Set this parameter equal to the name of the output database file from which the data are to be read. The file extension is optional.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the flux during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginnning of the step. 

INC

This parameter is relevant only when the FILE  parameter is used. 

Set this parameter equal to the increment in the selected step of the previous analysis from which the concentrated nodal fluxes will be read. By default, the concentrated nodal fluxes will be read from the last increment of the step specified on the STEP parameter or from the last step if the STEP parameter is omitted.

OP

Set OP=MOD (default) for existing [*CFLUX](ch03abk16.md)s to remain, with this option modifying existing fluxes or defining additional fluxes. 

Set OP=NEW if all existing [*CFLUX](ch03abk16.md)s applied to the model should be removed.

REGION TYPE

This parameter applies only to Abaqus/Explicit analyses.

This parameter is relevant only for concentrated fluxes applied on the boundary of an adaptive mesh domain. If concentrated fluxes are applied to nodes in the interior of an adaptive mesh domain, these nodes will always follow the material.

Set REGION TYPE=LAGRANGIAN (default) to apply a concentrated flux to a node that follows the material (nonadaptive).

Set REGION TYPE=SLIDING to apply a concentrated flux to a node that can slide over the material. Mesh constraints are typically applied to the node to fix it spatially.

Set REGION TYPE=EULERIAN to apply a concentrated flux to a node that can move independently of the material. This option is used only for boundary regions where the material can flow into or out of the adaptive mesh domain. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

STEP

This parameter is relevant only when the FILE parameter is used. 

Set this parameter equal to the step number of the previous analysis from which the concentrated nodal fluxes will be read. By default, the concentrated nodal fluxes will be read from the last step of the previous analysis.

### **Data lines to define a concentrated flux: **

**First line:**

Repeat this data line as often as necessary to define concentrated fluxes at different nodes and degrees of freedom.




