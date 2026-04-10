# *CONTACT CONTROLS ASSIGNMENT







### *CONTACT CONTROLS ASSIGNMENTAssign contact controls for the general contact algorithm.

This option is used to modify contact controls for specific contact interactions within the domain considered by the general contact algorithm in Abaqus/Explicit. It must be used in conjunction with the [*CONTACT](ch03abk54.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model or history data  

**Level: **Model,  Step

##### **References:**

- ["Contact controls for general contact in Abaqus/Explicit," Section 36.4.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactcontrolsassign)
- [*CONTACT](ch03abk54.md)

### **Required, mutually exclusive parameters: **

AUTOMATIC OVERCLOSURE RESOLUTION

Include this parameter to store offsets instead of adjusting nodes during initial overclosure resolution between surface pairs in the general contact domain.

CONTACT THICKNESS REDUCTION

Set CONTACT THICKNESS REDUCTION=SELF to limit automatic contact thickness reductions to only regions of potential self-contact and the perimeters of shell surfaces.

Set CONTACT THICKNESS REDUCTION=NOPERIMSELF to limit automatic contact thickness reductions to only regions of potential self-contact.

NODAL EROSION

Set NODAL EROSION=NO (default) to keep a node of an element-based surface in the general contact domain as a point mass after all contact faces and edges to which it is attached have eroded.

Set NODAL EROSION=YES to delete a node of an element-based surface from the general contact domain once all contact faces and edges to which it is attached have eroded.

ROTATIONAL TERMS

Set ROTATIONAL TERMS=NONE (default) to ignore the effects of shell and beam thickness offsets for frictional contact.

Set ROTATIONAL TERMS=STRUCTURAL for frictional contact to account for the incremental rotation of shell and beam thickness offsets in slip increment calculations and to apply a moment to nodes offset from the contact interface due to shell and beam thicknesses.

TYPE

Set TYPE=ENHANCED EDGE TRACKING (default) to activate the default tracking algorithm for edge-to-edge contact.

Set TYPE=EDGE TRACKING to activate an alternative tracking algorithm for edge-to-edge contact.

Set TYPE=FOLD TRACKING to activate the nondefault tracking algorithm for node-to-face contact.

Set TYPE=FOLD INVERSION CHECK to activate the fold inversion check.

Set TYPE=SCALE PENALTY to assign a scale factor to the default penalty stiffnesses.

### **Optional parameter: **

SEEDING

This parameter controls how the contact seeds are created on Lagrangian surfaces during a coupled Eulerian-Lagrangian analysis.

Set SEEDING=GLOBAL (default if adaptive mesh refinement is not activated) to create seeds on Lagrangian surfaces based on the smallest Eulerian element size in the entire Eulerian mesh; the seeding is performed once at the beginning of the analysis.

Set SEEDING=LOCAL to create seeds on Lagrangian surfaces based on the smallest Eulerian element size in the vicinity of the Lagrangian faces; the seeding is performed once for each face, as soon as a nearby Eulerian element is detected. 

Set SEEDING=DYNAMIC (default if adaptive mesh refinement is activated) to create seeds on Lagrangian surfaces based on the smallest Eulerian element size in the vicinity of the Lagrangian faces; the seed density is updated during the analysis.

### **Data lines for AUTOMATIC OVERCLOSURE RESOLUTION: **

**First line:**

Repeat this data line as often as necessary. If the contact controls assignments overlap, the last assignment applies in the overlap region.

### **No data lines are used with this option when the NODAL EROSION parameter is specified. **

### **Data lines for TYPE=FOLD TRACKING: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines for TYPE=FOLD INVERSION CHECK: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines for TYPE=SCALE PENALTY: **

**First line:**

Repeat this data line as often as necessary. If the contact controls assignments overlap, the last assignment applies in the overlap region.




