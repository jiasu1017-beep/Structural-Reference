# *CONTACT FORMULATION







### *CONTACT FORMULATIONSpecify a nondefault contact formulation for the general contact algorithm.

This option is used to modify the contact formulation for specific contact interactions within the domain considered by general contact. It must be used in conjunction with the [*CONTACT](ch03abk54.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; Model or history data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Model or Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Numerical controls for general contact in Abaqus/Standard," Section 36.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-agenlcontnumcontrolsstd)
- ["Contact formulation for general contact in Abaqus/Explicit," Section 38.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactformassign)
- [*CONTACT](ch03abk54.md)

### **Required parameter: **

TYPE

Set TYPE=EDGE TO EDGE to control the edge-to-edge (beam-to-beam) contact formulations used in Abaqus/Standard. This setting does not apply for Abaqus/Explicit.

Set TYPE=MASTER SLAVE ROLES to control master-slave roles for specific interactions in Abaqus/Standard. This setting does not apply for Abaqus/Explicit.

Set TYPE=PURE MASTER-SLAVE to specify that a contact interaction should use pure master-slave weighting for specific node-to-face contact surface pairs in Abaqus/Explicit. This setting does not apply for Abaqus/Standard.

Set TYPE=POLARITY to choose which sides of double-sided elements will be considered for node-to-face or Eulerian-Lagrangian contact with another surface in Abaqus/Explicit. This setting does not apply for Abaqus/Standard.

Set TYPE=SLIDING TRANSITION to control the smoothness of the surface-to-surface formulation upon sliding for specific interactions in Abaqus/Standard. This setting does not apply for Abaqus/Explicit.

### **Optional parameter: **

FORMULATION

This parameter applies only if TYPE=EDGE TO EDGE. It is used to activate the contact formulations to be used globally for edge-to-edge (beam-to-beam) contact.

Set FORMULATION=CROSS to activate an edge-to-edge contact formulation applicable to nonparallel beams that bases the contact normal direction on the cross product of the respective beam axial directions.

Set FORMULATION=RADIAL to activate an edge-to-edge contact formulation applicable to nearly parallel beams that bases the contact normal direction on a beam radial direction.

Set FORMULATION=BOTH to activate both edge-to-edge contact formulations.

Set FORMULATION=NO (default) to deactivate edge-to-edge contact formulations.

### **Data lines to control master-slave roles for contact interactions in Abaqus/Standard: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to assign pure master-slave roles to contact interactions in Abaqus/Explicit: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to assign polarity to contact interactions in Abaqus/Explicit: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to control the smoothness of the surface-to-surface formulation upon sliding for contact interactions in Abaqus/Standard: **

**First line:**

Repeat this data line as often as necessary.

### **There are no data lines to control the edge-to-edge (beam-to-beam) contact formulations in Abaqus/Standard. **




