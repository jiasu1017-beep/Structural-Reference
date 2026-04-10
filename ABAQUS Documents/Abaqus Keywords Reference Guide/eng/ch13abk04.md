# *MASS







### *MASSSpecify a point mass.

This option is used to define lumped mass values associated with MASS elements.

It is also used to define mass proportional damping (for direct-integration dynamic analysis and explicit dynamic analysis) and composite damping (for modal dynamic analysis) associated with MASS elements. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module.

##### **Reference:**

- ["Point masses," Section 30.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-emasses)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the MASS elements for which the value is being given.

### **Optional parameters: **

ALPHA

Set this parameter equal to the ![](../graphics/key_eqn00077.gif) factor to create mass proportional damping for the MASS elements when used in direct-integration dynamics or explicit dynamics. This value is ignored in modal dynamics. The default is 0.0.

COMPOSITE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the fraction of critical damping to be used with the MASS elements when calculating composite damping factors for the modes when used in mode-based analyses that are not based on the SIM architecture. The default is 0.0.

For mode-based analyses that are based on the SIM architecture, the [*COMPOSITE MODAL DAMPING](ch03abk27.md) option should be used instead. This value is ignored in direct-integration dynamics.

ORIENTATION

This parameter applies only when TYPE=ANISOTROPIC.

Set this parameter equal to the name of an [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) that is being used to define the principal directions of the anisotropic mass tensor. If the ORIENTATION parameter is omitted, it is assumed that the principal directions coincide with the global axes.

In a large-displacement analysis, the local axes of the anisotropic mass rotate with the rotation, if active, of the node to which the MASS element is attached.

TYPE

Set TYPE=ISOTROPIC (default) for an isotropic mass tensor.

Set TYPE=ANISOTROPIC for an anisotropic mass tensor with possibly three different principal values.

### **Data line to define the magnitude of an isotropic mass (not weight): **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.

### **Data line to define the three principal values of an anisotropic mass tensor (not weight): **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.




