# *CO-SIMULATION REGION







### *CO-SIMULATION REGIONIdentify the interface regions in the Abaqus model and specify the fields to be exchanged during co-simulation.

This option is used to identify the regions across which data will be exchanged and to specify the fields to be passed across those regions.  It must be used in conjunction with the [*CO-SIMULATION](ch03abk78.md) option to identify the analysis program for co-simulation with Abaqus. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Co-simulation: overview," Section 17.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationover)
- ["Preparing an Abaqus analysis for co-simulation," Section 17.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationprep)
- [*CO-SIMULATION](ch03abk78.md)

### Defining a co-simulation region for CO-SIMULATION, PROGRAM=MULTIPHYSICS or PROGRAM=MPCCI

### **Required, mutually exclusive parameters: **

EXPORT

When TYPE=NODE, SURFACE, or VOLUME, include this parameter to specify fields and the accompanying region for export to the coupled analysis. 

When TYPE=DISCRETE, include this parameter to specify sensor variables for export.

IMPORT

When TYPE=NODE, SURFACE, or VOLUME, include this parameter to specify fields and the accompanying region for import from the coupled analysis. 

When TYPE=DISCRETE, include this parameter to specify actuator variables for import.

### **Optional parameter: **

TYPE

Set TYPE=NODE to define a co-simulation region consisting of nodes only.

Set TYPE=SURFACE (default) to define a co-simulation surface region.

Set TYPE=VOLUME to define a co-simulation volume region.

Set TYPE=DISCRETE to define coupling through sensors and actuators.

### **Data lines for TYPE=NODE: **

**First line:**

Repeat this data line as often as necessary to define more than seven field identifiers for a given region. Repeat the option to define import and/or export fields. When PROGRAM=MULTIPHYSICS, only a single node set can be declared for the co-simulation.

### **Data lines for TYPE=SURFACE: **

**First line:**

Repeat this data line as often as necessary to define more than seven field identifiers for a given region. Repeat the option to define import and/or export fields. When PROGRAM=MULTIPHYSICS, only a single surface can be declared for the co-simulation.

### **Data lines for TYPE=VOLUME: **

**First line:**

Repeat this data line as often as necessary to define more than seven field identifiers for a given region. Repeat the option to define import and/or export fields. When PROGRAM=MULTIPHYSICS, only a single element set can be declared for the co-simulation.

### **Data lines for TYPE=DISCRETE: **

**First line:**

Repeat this data line as often as necessary to define more than seven sensor or actuator definitions. The data line can refer either to names of sensors only or to names of actuators only, according to the IMPORT or EXPORT parameter setting.

### Defining a co-simulation region for CO-SIMULATION, PROGRAM=ABAQUS

### **Optional parameter: **

TYPE

Set TYPE=SURFACE (default) to define a surface-based co-simulation region.

Set TYPE=NODE to define a co-simulation region using a node set.

### **Data line for TYPE=SURFACE: **

**First (and only) line:**

### **Data line for TYPE=NODE: **

**First (and only) line:**




