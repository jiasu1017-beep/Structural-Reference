# *BEAM ADDED INERTIA







### *BEAM ADDED INERTIADefine additional beam inertia.

This option is used in conjunction with the [*BEAM SECTION](ch02abk06.md) or [*BEAM GENERAL SECTION](ch02abk05.md) option to define additional mass and rotary inertia per unit length in shear flexible Timoshenko beam elements. This option is also used to define mass proportional damping (for direct-integration dynamic analysis) and in Abaqus/Standard composite damping (for modal dynamic analysis) associated with the added inertia.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

##### **References:**

- ["Choosing a beam element," Section 29.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamelem)
- ["Beam section behavior," Section 29.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamsectionbehavior)

### **Optional parameters: **

ALPHA

Set this parameter equal to the ![](../graphics/key_eqn00077.gif) factor to create inertia proportional damping for added inertia associated with this option when used in direct-integration dynamics. This value is ignored in modal dynamics. The default is ALPHA=0.0. (Units of [T1](../popups/usb-int-iconventions-unitsym.md).)

COMPOSITE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the fraction of critical damping to be used with the beam elements when calculating composite damping factors for the modes when used in modal dynamics.  The default is COMPOSITE=0.0.

This value is ignored in direct-integration dynamics. It is also ignored in mode-based analyses based on the SIM architecture, where the [*COMPOSITE MODAL DAMPING](ch03abk27.md) option should be used instead.

### **Data line to define additional beam inertia: **

**First line:**

The rotary inertia should be given in units of [ML](../popups/usb-int-iconventions-unitsym.md). Abaqus does not use any specific physical units, so the user's choice must be consistent.

Repeat this set of data lines as often as necessary to define the additional beam inertia.




