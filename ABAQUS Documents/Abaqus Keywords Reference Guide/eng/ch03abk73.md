# *CONTACT STABILIZATION







### *CONTACT STABILIZATIONDefine contact stabilization controls for general contact.

Multiple instances of the option can be used to define contact stabilization controls for general contact in Abaqus/Standard.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Stabilization for general contact in Abaqus/Standard," Section 36.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-agenlcontstabilize)
- [*CONTACT](ch03abk54.md)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines a time-dependent scale factor for contact stabilization over the step. If this parameter is omitted, the scale factor ramps linearly from unity to zero over the step.

RANGE

Set this parameter equal to the clearance at which the stabilization becomes zero; no contact stabilization is applied where the separation between surfaces exceeds this value. By default, this clearance is calculated by Abaqus/Standard based on the facet sizes on contact surfaces.

REDUCTION PER INCREMENT

Set this parameter equal to a factor by which Abaqus/Standard will reduce the contact stabilization coefficient per increment. The default value is 0.1 for the interactions specified on the data lines of this option.

RESET

Include this parameter to cancel carryover effects from contact stabilization specifications involving nondefault amplitudes that appeared in previous steps. This parameter cannot be used in conjunction with any other parameters. There are no data lines if this parameter is included.

SCALE FACTOR

Set this parameter equal to a factor by which Abaqus/Standard will scale the contact stabilization coefficient. The default value is unity for the interactions specified on the data lines of this option.

Set SCALE FACTOR=USER ADAPTIVE to scale the contact stabilization coefficient by a factor that decreases over iterations within each increment, according to the pattern specified on the data line.

TANGENT FRACTION

Set this parameter equal to a factor that scales the contact stabilization coefficient in the tangential direction only. The default value is zero, such that no contact stabilization is applied in the tangential direction.

### **Data lines if the RESET parameter is omitted: **

**First line:**

Repeat this data line as often as necessary. 

### **Data line if SCALE FACTOR=USER ADAPTIVE: **

**First line:**




