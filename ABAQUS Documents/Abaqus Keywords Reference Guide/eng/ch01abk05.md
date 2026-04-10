# *ADAPTIVE MESH CONSTRAINT







### *ADAPTIVE MESH CONSTRAINTSpecify constraints on the motion of the mesh for an adaptive mesh domain.

**Warning:**Abaqus/Explicit does not admit jumps in mesh displacement. If no amplitude is specified, Abaqus/Explicit will ignore the user-supplied displacement value and enforce a zero mesh motion constraint.

This option is used to prescribe independent mesh motion for nodes in an adaptive mesh domain or to define nodes that must follow the material. It can be used only in conjunction with the [*ADAPTIVE MESH](ch01abk04.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Displacement and velocity adaptive mesh constraints are supported in the Step module.

##### **References:**

- ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)
- ["Defining ALE adaptive mesh domains in Abaqus/Standard," Section 12.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aalestd)
- ["UMESHMOTION," Section 1.1.43 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uumeshmotion)
- [*ADAPTIVE MESH](ch01abk04.md)

### **Optional parameters: **

AMPLITUDE

This parameter is relevant only when some of the variables being prescribed have nonzero magnitudes. Set this parameter equal to the name of the amplitude curve defining the magnitude of the prescribed mesh motion (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

CONSTRAINT TYPE

Set CONSTRAINT TYPE=SPATIAL (default) to prescribe mesh motions that are independent of the underlying material.

Set CONSTRAINT TYPE=LAGRANGIAN to define nodes that must follow the material.

OP

Set OP=MOD (default) to modify existing mesh constraints or to add mesh constraints to degrees of freedom that were previously unconstrained.

Set OP=NEW if all mesh constraints that are currently in effect should be removed. To remove only selected mesh constraints, use OP=NEW and respecify all mesh constraints that are to be retained.

The OP parameter must be the same for all uses of the [*ADAPTIVE MESH CONSTRAINT](ch01abk05.md) option within a single step.

TYPE

Set TYPE=DISPLACEMENT (default) to prescribe mesh displacement.

Set TYPE=VELOCITY to prescribe mesh velocity.

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter if the mesh motion is to be defined in user subroutine [`UMESHMOTION`](../sub/sub-link.md#sub-xsl-umeshmotion). This parameter cannot be used when CONSTRAINT TYPE=LAGRANGIAN.

### **Data lines to prescribe mesh motions that are independent of the material (CONSTRAINT TYPE=SPATIAL): **

**First line:**

Repeat this data line as often as necessary to specify mesh constraints at different nodes and degrees of freedom.

### **Data lines to define nodes that must follow the material (CONSTRAINT TYPE=LAGRANGIAN): **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.




