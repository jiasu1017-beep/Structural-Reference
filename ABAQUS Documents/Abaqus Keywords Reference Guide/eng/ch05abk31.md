# *EULERIAN BOUNDARY







### *EULERIAN BOUNDARYDefine inflow and outflow conditions at Eulerian mesh boundaries.

This option is used to specify inflow and outflow conditions at the boundaries of an Eulerian mesh.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **Reference:**

- ["Defining Eulerian boundaries," Section 14.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeulerianboundary)

### **Optional parameters: **

INFLOW

Set INFLOW=FREE (default) if Eulerian material can flow freely into the Eulerian domain.

Set INFLOW=NONE if neither Eulerian material nor void can flow into the Eulerian domain.

Set INFLOW=VOID if only void can flow into the Eulerian domain.

OP

Set OP=MOD (default) to modify existing inflow/outflow conditions or to define additional inflow/outflow conditions.

Set OP=NEW to remove all existing inflow/outflow conditions.

OUTFLOW

This parameter is used to define boundary conditions in unbounded domain problems.

Set OUTFLOW=FREE (default if INFLOW=VOID) if Eulerian material can flow freely out of the Eulerian domain.

Set OUTFLOW=NONREFLECTING to specify a nonreflecting radiation boundary condition.

Set OUTFLOW=NONUNIFORM PRESSURE to specify an equilibrium condition at the boundary.

Set OUTFLOW=ZERO PRESSURE (default) to specify a zero pressure at the boundary.

### **Data lines to define the surface where Eulerian boundary conditions are applied: **

**First line:**

Repeat this data line as often as necessary to define inflow/outflow conditions for different surfaces.




