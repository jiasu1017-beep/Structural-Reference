# *ROTARY INERTIA







### *ROTARY INERTIADefine rigid body rotary inertia.

This option is used to define rigid body rotary inertia values associated with ROTARYI elements.

It is also used to define mass proportional damping (for direct-integration dynamic analysis and explicit dynamic analysis) and composite damping (for modal dynamic analysis) associated with ROTARYI elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module.

##### **Reference:**

- ["Rotary inertia," Section 30.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-erotinertia)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the ROTARYI elements for which the value is being given.

### **Optional parameters: **

ALPHA

Set this parameter equal to the ![](../graphics/key_eqn00077.gif) factor to create inertia proportional damping for the ROTARYI elements when used in direct-integration dynamics or explicit dynamics. This value is ignored in modal dynamics. The default is 0.0.

COMPOSITE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the fraction of critical damping to be used with the ROTARYI elements when calculating composite damping factors for the modes when used in modal dynamics. The default is 0.0.

This value is ignored in direct-integration dynamics. It is also ignored in mode-based analyses that are based on the SIM architecture, where the [*COMPOSITE MODAL DAMPING](ch03abk27.md) option should be used instead.

ORIENTATION

Set this parameter equal to the name of an [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that is being used to define the directions of the local axes for which the rotary inertia values are being given. If the ORIENTATION parameter is omitted, it is assumed that the components of the inertia tensor are being given with respect to the global axes; i.e., the global and local inertia axes coincide.

In large-displacement analysis (an Abaqus/Explicit analysis or when the NLGEOM parameter is included on the [*STEP](ch18abk36.md) option in an Abaqus/Standard analysis), the local axes of inertia rotate with the rotation of the node to which the ROTARYI element is attached.

### **Data line to define the rotary inertia: **

**First (and only) line:**

The rotary inertia should be given in units of [ML2](../popups/usb-int-iconventions-unitsym.md). Abaqus does not use any specific physical units, so the user's choice must be consistent.




