# *FLUID BOUNDARY







### *FLUID BOUNDARYSpecify boundary conditions for fluid flow analyses.

This option is used to specify boundary conditions for fluid flow analyses. Boundary conditions can be specified as spatially varying or constant with an associated variation in time.

**Products: **Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- ["Boundary conditions in Abaqus/CFD," Section 34.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundarycfd)
- [*CFD](ch03abk13.md)

### **Required parameter: **

TYPE

Set TYPE=ELEMENT to specify distributed boundary values at element faces.

Set TYPE=NODE to specify distributed boundary values at nodes.

Set TYPE=PHYSICAL to specify boundary values based on a physical type.

Set TYPE=SURFACE to specify boundary values at a surface. 

### **Required, mutually exclusive parameters for use with TYPE=PHYSICAL: **

PRESSUREOUTLET

Include this parameter to specify a pressure outlet boundary condition.

SYMMETRY

Include this parameter to specify a symmetry boundary condition.

VELOCITYINLET

Include this parameter to specify a velocity inlet boundary condition.

WALL

Include this parameter to specify a wall boundary condition.

### **Required parameter if TYPE=PHYSICAL: **

SURFACE

Set this parameter equal to the name of the surface on which to apply the boundary condition.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the boundary condition magnitude during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step. This parameter cannot be used when TYPE=PHYSICAL.

DISTRIBUTION

Set this parameter equal to a label that defines the distribution used in conjunction with the PVDEP boundary type (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)). This parameter is ignored if the boundary type is not PVDEP. This parameter cannot be used when TYPE=PHYSICAL.

OP

Set OP=MOD (default) for existing [*FLUID BOUNDARY](ch06abk17.md)s to remain, with this option modifying existing boundary conditions or defining additional boundary conditions.

Set OP=NEW if all existing [*FLUID BOUNDARY](ch06abk17.md)s applied to the model should be removed. New boundary conditions can be defined.

SLIP

The parameter can be used only if the WALL parameter is included. Set SLIP=NO (default) to indicate a no-slip wall boundary condition. Set SLIP=YES to indicate a slip wall boundary condition.

### **Data lines for TYPE=ELEMENT: **

**First line:**

Repeat this data line as often as necessary to specify fixed boundary conditions at different elements and degrees of freedom.

### **Data lines for TYPE=NODE: **

**First line:**

Repeat this data line as often as necessary to specify fixed boundary conditions at different nodes and degrees of freedom.

### **Data line for TYPE=PHYSICAL if the WALL and SLIP=NO parameters are included: **

**First (and only) line:**

### **Data lines for TYPE=PHYSICAL if the WALL and SLIP=YES parameters are included: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at the slip wall.

### **Data lines for TYPE=PHYSICAL if the PRESSUREOUTLET parameter is included: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at the pressure outlet.

### **Data lines for TYPE=PHYSICAL if the VELOCITYINLET parameter is included: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at the velocity inlet.

### **Data lines for TYPE=SURFACE: **

**First line:**

Repeat this data line as often as necessary to specify boundary conditions at different surfaces and degrees of freedom.

### **There are no data lines if the SYMMETRY parameter is specified. **




