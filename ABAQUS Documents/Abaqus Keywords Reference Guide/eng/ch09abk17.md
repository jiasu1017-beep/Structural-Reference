# *INERTIA RELIEF







### *INERTIA RELIEFApply inertia-based load balancing.

This option is used to apply inertia-based loads on a free or partially constrained body.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Inertia relief," Section 11.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ainertiarelief)
- ["Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed)

### **Optional parameters: **

ORIENTATION

Set this parameter equal to the name given to the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that specifies the orientation of the local system for rigid body degrees of freedom.

### **Optional, mutually exclusive parameters: **

FIXED

Include this parameter (default) to indicate that the inertia relief load from a previous step should remain fixed at its value from the beginning of the current step.

REMOVE

Include this parameter to indicate that the inertia relief load from a previous step should be removed in the current step.

### **Optional data lines to specify global (or local, if the ORIENTATION parameter is used) degrees of freedom that define the free directions along which inertia relief loads are applied: **

**First line:**

**Second line (only needed to define a reference point for the rigid body direction vectors when the user-chosen combination of free directions requires such a point):**

These data lines are needed only if rigid body motions are constrained in some directions.

### **There are no data lines when the FIXED or REMOVE parameters are specified. **




